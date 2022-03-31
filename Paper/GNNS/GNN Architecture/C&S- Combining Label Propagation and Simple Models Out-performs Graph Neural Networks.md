> ❝ 论文标题 ｜ Combining Label Propagation and Simple Models Out-performs Graph Neural Networks
> 论文来源 ｜ ICLR 2021, Cornell University，Facebook， 黄倩
> 论文链接 ｜ [https://arxiv.org/abs/2010.13993](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2010.13993)
> 源码链接 ｜ [https://github.com/CUAI/CorrectAndSmooth](https://link.zhihu.com/?target=https%3A//github.com/CUAI/CorrectAndSmooth)
>
> ❞

[C&S：标签传播思想与浅层模型相结合性能即可超过图神经网络 | 梦家博客 (dreamhomes.top)](https://dreamhomes.top/posts/202103251025/)

## 介绍

图神经网络 (GNNs) 在图表示学习领域盛极一时，但是对为什么 GNNs 有效或者其对不同任务性能提升的必然性知之甚少。这篇文章通过大量的直推式实验（节点分类任务）证明，通过浅层模型和两个基于标签传播的后处理步骤即可达到当前 GNNs 模型的性能 🤭，后处理步骤包括两步 (i) 误差修正 (error correlation)：利用训练数据中的残差来纠正测试数据中的误差 (ii) 预测修正 (prediction correlation)：平滑测试数据中的预测结果，作者将其提出的整个框架总称为 C&S（correct and Smooth），并且在实验中证明 C&S 不仅准确性超过当前主流的 GNNs 模型，而且参数量和运行时间远远低于复杂的 GNNs 结构。

## 算法\模型

![C&S 算法流程](https://cdn.jsdelivr.net/gh/Zhangxin98/Note@main/img/202112021757621.png)

主要包含三个部分：

* 基础预测模型：仅依赖节点特征并且忽略图的结构，例如 MLP 或者线性模型；

* 修正步骤：将训练数据中的不确定性传播到整个图以此来修正基础预测结果；

* 平滑步骤：对节点预测结果进行平滑。


​    

其中修正步骤和平滑步骤是基于半监督学习的标签传播思想进行改进的，整个框架没有利用图结构来学习模型参数因此参数量非常少而且不需要大量的时间来训练模型，但实验效果却非常好。

下面详细介绍下 C&S 模型的细节：

### C&S  Model

> [论文笔记：ICLR 2021 Combining Lable Propagation And Simple Models Out-Performs Graph Neural Network_饮冰l的博客-CSDN博客](https://blog.csdn.net/qq_44015059/article/details/113689870)

