# arXiv AI Digest

本项目用于在本地自动抓取 arXiv 上最近一段时间内的 AI 相关论文，并对论文进行结构化归纳。

当前冻结的产品方向如下：

- 默认查询最近 `14` 天论文，可在 UI 中手动修改。
- 默认全文分析阈值为 `20` 篇，可在 UI 中手动修改。
- 当筛选后的论文数大于阈值时，先只做摘要分析。
- 当筛选后的论文数小于等于阈值时，优先做全文分析。
- 支持用户手动勾选论文，触发单篇或多篇论文的详细分析。
- 支持用户手动维护包含关键词和排除关键词。
- 本地使用数据库和文件存储记录，便于后续检索、筛选和导出。
- 多篇聚合思维导图作为独立功能，放在第二阶段实现。

建议的第一阶段技术选型：

- `Python`
- `Streamlit` 本地 UI
- `SQLite` 本地数据库
- `PyMuPDF` 或同类 PDF 文本提取工具
- 大模型接口用于摘要/全文归纳

详细设计见：

- [设计说明](docs/design-spec.md)

## Quick Start

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -e .
streamlit run main.py
```

## Current Status

- Project skeleton is ready.
- SQLite bootstrap is implemented.
- Settings and keyword management UI are implemented.
- Manual arXiv URL and local PDF registration are implemented.
- arXiv sync is implemented and writes papers plus queued analysis jobs to the local database.
- PDF parsing workflow and model summarization are the next steps.
