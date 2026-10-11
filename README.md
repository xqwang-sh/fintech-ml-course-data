# 金融科技概论：课程数据

这是《金融科技概论》机器学习部分的学生数据仓库。数据分成两类：课堂讲义使用的固定样本，以及课程项目使用的固定版本数据。

## 获取数据

在讲义源文件所在目录的上一级执行：

```bash
git clone https://github.com/xqwang-sh/fintech-ml-course-data.git data
```

如果你已经有一个名为 `data` 的目录，请先确认其中没有同名课程数据，再执行：

```bash
git -C data pull
```

这样，讲义中的相对路径可以直接使用：

```python
import pandas as pd

classroom = pd.read_parquet(
    "../data/releases/classroom/v1/data/california_base.parquet"
)
project_train = pd.read_parquet(
    "../data/releases/projects/v1/data/loan-approval/student_train.parquet"
)
```

所有数据文件都是 Parquet。`pandas.read_parquet()` 可以读取它们。若本机尚未安装 Parquet 读取引擎，请安装 `pyarrow`。

## 两类数据在哪里

| 数据类别 | 路径 | 用途 |
|---|---|---|
| 课堂数据 | `releases/classroom/v1/data/` | W10–W15 的课堂讲义和上机练习 |
| 项目数据 | `releases/projects/v1/data/` | 五个可以直接获取数据的课程项目 |

### 课堂数据

- `california_base.parquet`：California Housing 固定课堂样本。
- `california_dirty.parquet`：包含人为设置的数据问题，用于清洗和诊断练习。
- `uci_credit_base.parquet`：UCI 信用卡违约固定课堂样本。
- `uci_credit_with_leak.parquet`：加入 `post_default_collection_calls` 的教学版本，只用于讨论数据泄露。

### 项目数据

每个项目目录包含两个文件：

- `student_train.parquet`：包含特征、`course_row_id` 和目标，用于建模与本地验证。
- `student_hidden_features.parquet`：只包含特征和 `course_row_id`。确定最终方案后，使用它生成预测结果。

目前公开的数据项目为：

`loan-approval`、`loan-payback`、`bank-marketing`、`insurance-premium`、`lending-club`。

Home Credit Stability 项目暂不把数据上传到 GitHub。该竞赛的官方规则将数据使用限制在竞赛参与和 Kaggle 论坛范围内，因此不能公开再分发。项目说明仍保留这个选项，但选它前请向任课教师获取合规的数据访问方式。

## 版本和检查

每个版本目录都有以下文件：

- `manifest.yaml`：数据文件、行数和 SHA-256 校验值；
- `schema.yaml`：任务和字段说明；
- `quality.yaml`：发布检查结果；
- `lineage.yaml`：课程版本的生成说明；
- `checksums.sha256`：公开文件的完整校验清单。

本仓库不包含教师隐藏标签、教师变更日志、原始下载包或内部数据处理文件。不要尝试从 `student_hidden_features.parquet` 推断隐藏标签，也不要把隐藏标签放入学生项目仓库或 AI 对话。

来源和再分发说明见 [NOTICE.md](NOTICE.md)。
