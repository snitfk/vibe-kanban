<p align="center">
  <a href="https://vibekanban.com">
    <picture>
      <source srcset="frontend/public/vibe-kanban-logo-dark.svg" media="(prefers-color-scheme: dark)">
      <source srcset="frontend/public/vibe-kanban-logo.svg" media="(prefers-color-scheme: light)">
      <img src="frontend/public/vibe-kanban-logo.svg" alt="Vibe Kanban Logo">
    </picture>
  </a>
</p>

<p align="center">让 Claude Code、Gemini CLI、Codex、Amp 和其他编码助手发挥 10 倍效能...</p>
<p align="center">
  <a href="https://www.npmjs.com/package/vibe-kanban"><img alt="npm" src="https://img.shields.io/npm/v/vibe-kanban?style=flat-square" /></a>
  <a href="https://github.com/BloopAI/vibe-kanban/blob/main/.github/workflows/publish.yml"><img alt="Build status" src="https://img.shields.io/github/actions/workflow/status/BloopAI/vibe-kanban/.github%2Fworkflows%2Fpublish.yml" /></a>
  <a href="https://deepwiki.com/BloopAI/vibe-kanban"><img src="https://deepwiki.com/badge.svg" alt="Ask DeepWiki"></a>
</p>

<h1 align="center">
  <a href="https://jobs.polymer.co/vibe-kanban?source=github"><strong>我们正在招聘!</strong></a>
</h1>

![](frontend/public/vibe-kanban-screenshot-overview.png)

## 概述

AI 编码助手正在越来越多地编写世界上的代码,人类工程师现在将大部分时间花在规划、审查和编排任务上。Vibe Kanban 简化了这一过程,使您能够:

- 轻松在不同的编码助手之间切换
- 编排多个编码助手的并行或顺序执行
- 快速审查工作并启动开发服务器
- 跟踪编码助手正在处理的任务状态
- 集中配置编码助手的 MCP 配置
- 在远程服务器上运行 Vibe Kanban 时通过 SSH 远程打开项目

您可以在[这里](https://youtu.be/TFT3KnZOOAk)观看视频概述。

## 安装

确保您已通过您喜欢的编码助手进行身份验证。完整的支持编码助手列表可以在[文档](https://vibekanban.com/docs)中找到。然后在终端中运行:

```bash
npx vibe-kanban
```

## 文档

请访问[网站](https://vibekanban.com/docs)获取最新的文档和用户指南。

## 支持

我们使用 [GitHub Discussions](https://github.com/BloopAI/vibe-kanban/discussions) 进行功能请求。请开启讨论以创建功能请求。对于 bug,请在此仓库中开启 issue。

## 贡献

我们希望想法和更改首先通过 [GitHub Discussions](https://github.com/BloopAI/vibe-kanban/discussions) 或 [Discord](https://discord.gg/AC4nwVtJM3) 与核心团队提出,我们可以在那里讨论实现细节以及与现有路线图的协调。请不要在未与团队讨论您的提案之前打开 PR。

## 开发

### 前置要求

- [Rust](https://rustup.rs/) (最新稳定版)
- [Node.js](https://nodejs.org/) (>=18)
- [pnpm](https://pnpm.io/) (>=8)

额外的开发工具:
```bash
cargo install cargo-watch
cargo install sqlx-cli
```

安装依赖:
```bash
pnpm i
```

### 运行开发服务器

```bash
pnpm run dev
```

这将启动后端。将从 `dev_assets_seed` 文件夹复制一个空白数据库。

### 构建前端

仅构建前端:

```bash
cd frontend
pnpm build
```

### 从源代码构建 (macOS)

1. 运行 `./local-build.sh`
2. 使用 `cd npx-cli && node bin/cli.js` 测试


### 环境变量

以下环境变量可以在构建时或运行时配置:

| 变量 | 类型 | 默认值 | 描述 |
|----------|------|---------|-------------|
| `POSTHOG_API_KEY` | 构建时 | 空 | PostHog 分析 API 密钥(如果为空则禁用分析) |
| `POSTHOG_API_ENDPOINT` | 构建时 | 空 | PostHog 分析端点(如果为空则禁用分析) |
| `PORT` | 运行时 | 自动分配 | **生产环境**: 服务器端口。**开发环境**: 前端端口(后端使用 PORT+1) |
| `BACKEND_PORT` | 运行时 | `0` (自动分配) | 后端服务器端口(仅开发模式,覆盖 PORT+1) |
| `FRONTEND_PORT` | 运行时 | `3000` | 前端开发服务器端口(仅开发模式,覆盖 PORT) |
| `HOST` | 运行时 | `127.0.0.1` | 后端服务器主机 |
| `DISABLE_WORKTREE_ORPHAN_CLEANUP` | 运行时 | 未设置 | 禁用 git worktree 清理(用于调试) |

**构建时变量**必须在运行 `pnpm run build` 时设置。**运行时变量**在应用程序启动时读取。

### 远程部署

在远程服务器上运行 Vibe Kanban 时(例如,通过 systemctl、Docker 或云托管),您可以配置编辑器以通过 SSH 打开项目:

1. **通过隧道访问**: 使用 Cloudflare Tunnel、ngrok 或类似工具公开 Web UI
2. **在设置 → 编辑器集成中配置远程 SSH**:
   - 将**远程 SSH 主机**设置为您的服务器主机名或 IP
   - 将**远程 SSH 用户**设置为您的 SSH 用户名(可选)
3. **前置要求**:
   - 从本地计算机到远程服务器的 SSH 访问
   - 已配置 SSH 密钥(无密码身份验证)
   - VSCode Remote-SSH 扩展

配置后,"在 VSCode 中打开"按钮将生成类似 `vscode://vscode-remote/ssh-remote+user@host/path` 的 URL,这些 URL 会打开您的本地编辑器并连接到远程服务器。

有关详细设置说明,请参阅[文档](https://vibekanban.com/docs/configuration-customisation/global-settings#remote-ssh-configuration)。
