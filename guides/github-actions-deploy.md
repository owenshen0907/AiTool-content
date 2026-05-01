# GitHub Actions 自动部署

`AiTool-content` 是内容仓。生产服务器已经把 `/home/AiTool-content` 挂载到 AiTool 容器的 `/AiTool-content`，而 `/notes` 页面使用动态读取，所以内容仓更新后不需要重新构建 Next.js 镜像。

当前自动部署策略：

1. 本地写 Markdown。
2. push 到 `AiTool-content/main`。
3. GitHub Actions 通过 SSH 登录生产服务器。
4. 在服务器 `/home/AiTool-content` 执行 `git pull --ff-only origin main`。
5. 校验服务器 HEAD 是否等于本次 GitHub commit。
6. 请求 `/notes` 做一次健康检查。

## 需要配置的 Repository Secrets

在 GitHub 仓库 `owenshen0907/AiTool-content` 里进入：

`Settings > Secrets and variables > Actions > New repository secret`

必填：

- `PROD_SSH_HOST`：生产服务器 host 或 IP。
- `PROD_SSH_KEY`：GitHub Actions 使用的 SSH 私钥。建议使用专门的 deploy key，不要复用个人常用私钥。

可选：

- `PROD_SSH_PORT`：默认 `322`。
- `PROD_SSH_USER`：默认 `aitooldeploy`。
- `PROD_CONTENT_PATH`：默认 `/home/AiTool-content`。
- `PROD_HEALTHCHECK_URL`：默认 `https://owenshen.top/notes`。

## 推荐的 SSH key 做法

在本机生成一把专用 key：

```bash
ssh-keygen -t ed25519 -C "github-actions-aitool-content" -f ~/.ssh/aitool-content-actions
```

把公钥加入生产服务器允许登录的账号。生产环境建议使用专用部署用户，例如 `aitooldeploy`：

```bash
ssh-copy-id -i ~/.ssh/aitool-content-actions.pub -p 322 aitooldeploy@<PROD_SSH_HOST>
```

把私钥内容写入 GitHub Secret：

```bash
cat ~/.ssh/aitool-content-actions
```

复制完整输出，保存为 `PROD_SSH_KEY`。

## 为什么不在内容仓里重建 Docker

`AiTool` 的代码仓和 `AiTool-content` 的内容仓职责不同：

- 内容变更：只需要更新服务器上的 `/home/AiTool-content`。
- 网站代码变更：才需要在 `/home/AiTool` 重建 Docker 镜像并重启容器。

如果后续需要“站点代码 push 后自动重建”，应该在 `AiTool` 仓库单独添加一个部署 workflow，执行 `/home/AiTool/full-update.sh` 或等价的 Docker Compose 更新脚本。
