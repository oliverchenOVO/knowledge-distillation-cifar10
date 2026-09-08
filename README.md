# CIFAR-10 Knowledge Distillation

這是大學「人工智慧實務」課程的知識蒸餾實驗。目標是把大型 teacher 的知識轉移給參數量約十分之一的 student，在不增加推論模型大小的前提下改善 CIFAR-10 準確率。

## 实验结果

| 模型 | 参数量 | CIFAR-10 准确率 |
| --- | ---: | ---: |
| Teacher | 11,173,962 | **95.71%** |
| Student（未蒸馏） | 1,116,970 | **75.74%** |
| Student（知识蒸馏） | 1,116,970 | **80.20%** |

知识蒸馏让 student 提升 **4.46 个百分点**；student 参数量约减少 90%。这些数值来自本仓库 Notebook 保存的课程实验输出，可能因硬体、随机种子与套件版本而略有差异。

## 方法

- 以较深的卷积网络担任 teacher，较小的卷积网络担任 student。
- 先分别训练 teacher 与未蒸馏 student，建立基准。
- 蒸馏训练同时使用真实标签、temperature-scaled soft targets 与空间 attention transfer。
- 以相同 CIFAR-10 测试集比较 teacher、baseline student 与 distilled student。

![训练记录](results/training_history.png)

![准确率比较](results/accuracy_comparison.png)

## 运行方式

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab notebooks/knowledge_distillation_cifar10.ipynb
```

Notebook 使用 `torchvision.datasets.CIFAR10(..., download=True)` 下载资料。仓库不包含 CIFAR-10 压缩档、解压资料或约 85 MB 的 teacher checkpoint；运行 Notebook 即可重新训练。

## 资料与公开注意事项

资料来源、引用方式与公开前检查请见：

- [CIFAR-10 资料说明](docs/DATA_SOURCES.md)
- [GitHub 公开前检查](docs/PUBLICATION_CHECKLIST.md)

课程提供的起始架构或说明若不是本人原创，应在将仓库改为公开前取得教师同意并清楚标示；本准备包只保留最终实验 Notebook 与本人产生的结果图。
