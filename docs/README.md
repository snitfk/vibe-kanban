# Mintlify 入门套件

**[Mintlify 快速入门指南](https://starter.mintlify.com/quickstart)**

## 开发

安装 [Mintlify CLI](https://www.npmjs.com/package/mint) 以在本地预览您的文档更改。要安装,请使用以下命令:

```
npm i -g mint
```

在您的文档根目录(即 `docs.json` 所在的位置)运行以下命令:

```
mint dev
```

在 `http://localhost:3000` 查看您的本地预览。

## 发布更改

从您的[控制面板](https://dashboard.mintlify.com/settings/organization/github-app)安装我们的 GitHub 应用,以将更改从您的仓库传播到您的部署。推送到默认分支后,更改会自动部署到生产环境。

## 需要帮助?

### 故障排除

- 如果您的开发环境无法运行: 运行 `mint update` 以确保您拥有最新版本的 CLI。
- 如果页面加载为 404: 确保您在包含有效 `docs.json` 的文件夹中运行。

### 资源
- [Mintlify 文档](https://mintlify.com/docs)
- [Mintlify 社区](https://mintlify.com/community)
