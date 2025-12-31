# 远程服务

`remote` crate 包含 Vibe Kanban 托管 API 的实现。

## 前置要求

在仓库根目录创建 `.env.remote` 文件:

```env
VIBEKANBAN_REMOTE_JWT_SECRET=your_base64_encoded_secret
SERVER_PUBLIC_BASE_URL=http://localhost:3000
GITHUB_OAUTH_CLIENT_ID=your_github_web_app_client_id
GITHUB_OAUTH_CLIENT_SECRET=your_github_web_app_client_secret
GOOGLE_OAUTH_CLIENT_ID=your_google_web_app_client_id
GOOGLE_OAUTH_CLIENT_SECRET=your_google_web_app_client_secret
```

使用 `openssl rand -base64 48` 生成一次 `VIBEKANBAN_REMOTE_JWT_SECRET` 并将值复制到 `.env.remote`。

必须至少配置一个 OAuth 提供商(GitHub 或 Google)。

## 在本地运行堆栈

```bash
docker compose --env-file .env.remote -f docker-compose.yml up --build
```
在 `http://localhost:8081` 上公开 API。Postgres 服务在 `postgres://remote:remote@localhost:5432/remote` 可用。

## 运行 Vibe Kanban

```bash
export VK_SHARED_API_BASE=http://localhost:8081

pnpm run dev
```
