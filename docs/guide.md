# 使用指南

## 日常修改流程

1. 修改 docs 目录中的 Markdown 文件。
2. 在本地预览并检查页面及链接。
3. 提交修改并推送到 main 分支。
4. 在 Actions 页面查看构建与部署状态。
5. 打开网站检查内容是否更新。

这五步里只有第 1 步是「写作」，其余都是可以被流水线接管的机械动作。

## 常用命令

- `python -m mkdocs serve`：本地预览。
- `python -m mkdocs build --strict`：构建网站并严格检查警告。

## 一套完整的本地命令

```bash
# Windows PowerShell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt

# 构建（--strict：把警告当错误，提前发现问题链接）
python -m mkdocs build --strict

# 预览，默认 http://127.0.0.1:8000/
python -m mkdocs serve
```

## 推送发布

```bash
git status
git add docs mkdocs.yml requirements.txt .gitignore .github/workflows/deploy.yml README.md
git diff --staged
git commit -m "更新文档内容"
git push origin main
```

推送后到仓库的 Actions 页面看最新一次运行：`build` 成功才会执行 `deploy`，`deploy` 成功后会给出 `github-pages` 环境的地址。

## 常见问题

| 现象 | 排查方向 |
| --- | --- |
| 推送后 Actions 没有运行 | 改动是否落在 `docs/**`、`mkdocs.yml`、`requirements.txt` 或工作流文件上；只改 README 或 report 不会触发 |
| build 失败 | 展开日志看 `mkdocs build` 的输出，常见是导航里写了不存在的文件、链接失效 |
| 网站 404 | Settings → Pages 的来源是否为 GitHub Actions，deploy 任务是否成功 |
| 页面还是旧内容 | 浏览器缓存，强制刷新或用无痕窗口 |

## 小结

最省心的习惯是：**每次只改 `docs/` 下的文件，并且永远用 `--strict` 构建**。这样本地能过的，线上基本也能过。

回到 [首页](index.md)，或看看 [API 参考](api.md)。
