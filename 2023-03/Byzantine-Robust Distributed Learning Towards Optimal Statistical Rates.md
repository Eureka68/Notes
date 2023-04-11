本文主要提出了Median-based Gradient Descent Trimmed-mean-based Gradient Descent两种拜占庭容错聚合算法，并证明了他们所能达到的最低错误率。

其中Median-based Gradient Descent在聚合梯度时，选取所有梯度ω_k^i在第k个维度上的中位数，作为其聚合后梯度在第k个维度上的值。

其中Trimmed-mean-based Gradient Descent在聚合梯度时，需要提供参数β（表示系统中可能存在的拜占庭节点百分比），在所有梯度ω_k^i的每个维度k筛除掉最小的β*n个值和最大的β*n个值，再用剩下的值求平均作为聚合后梯度在第k个维度上的值。

理论证明Trimmed-mean-based Gradient Descent能够达到最低的错误率，而Median-based Gradient Descent在更加弱的假设下能达到接近最低的错误率。

其次，本文也将Median-based Gradient Descent应用于一轮联邦学习中，实验表明其也能在这种场景中进行安全聚合。
