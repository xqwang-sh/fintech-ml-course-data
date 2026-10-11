# 课程项目数据 v1

这些文件用于课程项目。项目页中的相对路径都指向这里。

每个项目目录有两个文件：

- `student_train.parquet`：有目标列，用于训练、验证和交叉验证；
- `student_hidden_features.parquet`：没有目标列，只在最终方案锁定后生成预测。

| 项目 | 任务 | 训练行数 | 隐藏特征行数 | 目标列 |
|---|---|---:|---:|---|
| `loan-approval` | 分类 | 46,916 | 11,729 | `loan_status` |
| `loan-payback` | 分类 | 475,195 | 118,799 | `loan_paid_back` |
| `bank-marketing` | 分类 | 600,000 | 150,000 | `y` |
| `insurance-premium` | 回归 | 960,000 | 240,000 | `Premium Amount` |
| `lending-club` | 分类 | 321,690 | 78,310 | `default` |

Home Credit Stability 暂不在这个公开目录中。原因和合规要求见仓库根目录的 [NOTICE.md](../../../NOTICE.md) 和课程讲义的项目页。

教师隐藏标签不会发布。你只能提交使用 `student_hidden_features.parquet` 生成的预测文件，不能自行评估隐藏行的真实标签。
