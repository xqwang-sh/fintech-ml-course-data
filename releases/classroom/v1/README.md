# 课堂数据 v1

这些固定样本用于 W10–W15 的讲义和上机练习。课堂代码从 `book/` 目录运行时，路径写成 `../data/releases/classroom/v1/data/...`。

| 文件 | 行数 | 用途 |
|---|---:|---|
| `california_base.parquet` | 2,000 | 回归、基线、验证和测试 |
| `california_dirty.parquet` | 2,000 | 数据清洗和异常诊断 |
| `uci_credit_base.parquet` | 5,000 | 分类、概率、阈值和模型比较 |
| `uci_credit_with_leak.parquet` | 5,000 | 识别人为加入的泄露字段 |

每个文件都有固定的 `split` 列。不要重新随机切分后再和讲义结果比较。
