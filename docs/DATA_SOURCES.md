# CIFAR-10 资料来源

本实验使用 [CIFAR-10 官方资料集](https://www.cs.toronto.edu/~kriz/cifar.html)，作者为 Alex Krizhevsky、Vinod Nair 与 Geoffrey Hinton。资料集共有 60,000 张 32×32 彩色图片，分为 10 类；其中 50,000 张用于训练、10,000 张用于测试。

建议引用官方技术报告：

> Krizhevsky, A. (2009). *Learning Multiple Layers of Features from Tiny Images*. University of Toronto. [PDF](https://www.cs.toronto.edu/~kriz/learning-features-2009-TR.pdf)

仓库不重新散布 CIFAR-10 档案。Notebook 会透过 torchvision 从官方来源下载到本机 `data/`，该资料夹已列入 `.gitignore`。若要发布、教学或商业使用，请自行确认官方页面与下载档内当时适用的条款。
