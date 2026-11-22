# 关于本项目

## 项目目标

实现从 Markdown 文档到公开网站的自动化发布。

目标很具体：改一行文字，推一次代码，几分钟后网页上就能看到变化，全程不碰服务器、不手工上传文件。

## 技术组成

| 工具 | 作用 |
| --- | --- |
| Markdown | 编写文档内容 |
| MkDocs Material | 将文档构建成静态网站 |
| GitHub Actions | 自动执行安装、构建和部署 |
| GitHub Pages | 托管并提供网站访问地址 |

## 四个部分怎么串起来

1. **源码**：`docs/` 目录下的四个 Markdown 文件，加上根目录的 `mkdocs.yml`，它们是人写的部分。
2. **构建产物**：`python -m mkdocs build` 生成的 `site/` 目录，里面有 HTML、CSS、JS 和搜索索引。它是机器生成的，所以写进 `.gitignore`，不提交。
3. **工作流**：`.github/workflows/deploy.yml` 描述「什么时候、按什么顺序、用哪些权限」把源码变成产物，再把产物交给 Pages。
4. **托管网站**：GitHub Pages 读取工作流上传的 artifact 并对外提供网址 `https://orihamaru.github.io/my-docs/`。

理解这条链路后，排错就变成了「定位是哪一段出了问题」：页面没更新，先看 Actions 有没有跑，再看 build 有没有成功，最后看 deploy 和缓存。

## 为什么用官方 Pages Actions

早期做法是把 `site/` 推到 `gh-pages` 分支再让 Pages 从分支发布，需要额外的分支管理和权限配置。本次使用 GitHub 官方提供的 `configure-pages` + `upload-pages-artifact` + `deploy-pages` 三件套：工作流里声明 `pages: write` 与 `id-token: write` 即可，不需要建分支、不需要 PR 审批、也不需要自己申请令牌。

## 我自己的补充

我把这个站点当成「随时可以修改的实验记录」：先保证流水线稳定，再慢慢往里加内容。下一步打算加一个标签页和站内搜索的快捷键说明，这些同样只需要改 Markdown 并推送。

返回 [首页](index.md)，或继续看 [使用指南](guide.md)。
