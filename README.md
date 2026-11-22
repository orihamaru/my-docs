# my-docs

## 项目简介

我的个人技术文档站。文档用 Markdown 编写，MkDocs Material 负责构建成静态网站，GitHub Actions 在每次推送到 `main` 时自动构建并部署到 GitHub Pages，不需要手工上传或维护额外的发布分支。

- **网站地址**：https://orihamaru.github.io/my-docs/
- **个人实验报告**：[个人实验报告](report/README.md)
- **文档源码**：`docs/`（四个页面：首页 / 关于 / 使用指南 / API 参考）

## 目录结构

```text
my-docs/
├── .github/workflows/deploy.yml   # 构建 + 部署工作流
├── docs/                          # 网站内容（手写 Markdown）
│   ├── index.md
│   ├── about.md
│   ├── guide.md
│   └── api.md
├── report/                        # 实践报告与截图
│   ├── README.md
│   └── images/
├── mkdocs.yml                     # 站点配置与导航
├── requirements.txt               # 构建依赖
└── .gitignore                     # 忽略 site/ 与 .venv/
```

## 本地预览

```bash
python -m venv .venv
# Windows PowerShell: .\.venv\Scripts\Activate.ps1
# macOS / Linux:     source .venv/bin/activate
python -m pip install -r requirements.txt
python -m mkdocs serve
```

打开 http://127.0.0.1:8000/ 预览。

## 构建检查

```bash
python -m mkdocs build --strict
```

`site/` 为构建产物，不提交到仓库；推送 `docs/`、`mkdocs.yml`、`requirements.txt` 或工作流文件到 `main` 会自动触发部署。
