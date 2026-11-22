# 我的技术文档

欢迎访问我的个人文档网站。本网站使用 MkDocs 构建，通过 GitHub Actions 自动部署到 GitHub Pages。

- 作者：orihamaru
- 实践主题：静态文档自动部署
- [关于本项目](about.md)
- [使用指南](guide.md)
- [API 参考](api.md)

## 这个站点是怎么来的

我平时写的笔记大多散落在本地 Markdown 文件里，既不方便分享，也没法在手机上看。这次实践我把「写文档」和「发布文档」拆成两件事：

| 我做的事 | 工具接手的事 |
| --- | --- |
| 只写 `docs/` 里的 Markdown | MkDocs 把 Markdown 转成 HTML |
| 推送 `main` 分支 | GitHub Actions 自动安装依赖并构建 |
| 打开网址检查内容 | GitHub Pages 托管 `site/` 构建产物 |

写作时我只关心内容本身，排版、导航、搜索、部署这些重复劳动交给流水线，这是这次实践最大的收获。

## 站点导航

- [关于本项目](about.md)：这个文档站的目标与技术组成
- [使用指南](guide.md)：修改文档、本地预览、推送发布的完整流程
- [API 参考](api.md)：一份用于练习接口描述的示例文档

## 本地预览

```bash
python -m venv .venv
python -m pip install -r requirements.txt
python -m mkdocs serve
```

更多命令见 [使用指南](guide.md)，仓库结构与报告见 [project README](https://github.com/orihamaru/my-docs)。


## 自动部署验证

自动部署验证：这段文字是我在 2026-11-22 第二次推送后新增的内容，用来确认 push 会自动触发构建并更新网站。
