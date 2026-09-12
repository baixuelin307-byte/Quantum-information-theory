# 4.1 State Distinguishing

## 1. 什么是 State Distinguishing？

State distinguishing（量子态区分）研究的是：

> 已知一个未知 qubit 来自若干候选量子态之一，如何通过测量判断它原来到底是哪一个状态。

基本流程可以理解为：

$$
\text{给一个未知量子态}
\rightarrow
\text{知道它来自几个候选态}
\rightarrow
\text{选择测量基}
\rightarrow
\text{根据测量结果猜原状态}
$$

---

## 2. 最简单的情况：区分 $|+\rangle$ 和 $|-\rangle$

定义：

$$
|+\rangle
=
\frac{1}{\sqrt{2}}|0\rangle
+
\frac{1}{\sqrt{2}}|1\rangle
$$

$$
|-\rangle
=
\frac{1}{\sqrt{2}}|0\rangle
-
\frac{1}{\sqrt{2}}|1\rangle
$$

写成二维向量：

$$
|+\rangle
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
1
\end{bmatrix}
$$

$$
|-\rangle
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
-1
\end{bmatrix}
$$

因此在二维图中：

- $|+\rangle$：右上方向
- $|-\rangle$：右下方向

计算内积：

$$
\langle +|-\rangle = 0
$$

所以：

$$
|+\rangle \perp |-\rangle
$$

也就是说，$|+\rangle$ 和 $|-\rangle$ 是正交态。
