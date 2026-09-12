# 4.1 State Distinguishing

## 1. 什么是 State Distinguishing？

State distinguishing（量子态区分）研究的是：

> 已知一个未知 qubit 来自若干候选量子态之一，如何通过测量判断它原来到底是哪一个状态。

基本流程可以理解为：

`给一个未知量子态 → 知道它来自几个候选态 → 选择测量基 → 根据测量结果猜原状态`

---

## 2. 最简单的情况：区分 $|+\rangle$ 和 $|-\rangle$

定义：

$|+\rangle=\frac{1}{\sqrt{2}}|0\rangle+\frac{1}{\sqrt{2}}|1\rangle$

$|-\rangle=\frac{1}{\sqrt{2}}|0\rangle-\frac{1}{\sqrt{2}}|1\rangle$

写成二维向量：

$|+\rangle=\frac{1}{\sqrt{2}}\begin{bmatrix}1\\1\end{bmatrix}$

$|-\rangle=\frac{1}{\sqrt{2}}\begin{bmatrix}1\\-1\end{bmatrix}$

因此在二维图中：

- $|+\rangle$：右上方向
- $|-\rangle$：右下方向

计算内积：

$\langle +|-\rangle=0$

所以：

$|+\rangle\perp|-\rangle$

也就是说，$|+\rangle$ 和 $|-\rangle$ 是正交态。

---

## 3. 为什么直接测量 $0/1$ 不能区分 $|+\rangle$ 和 $|-\rangle$？

如果使用 computational basis：

$\{|0\rangle,|1\rangle\}$

测量 $|+\rangle$：

$P(0)=\frac{1}{2},\quad P(1)=\frac{1}{2}$

测量 $|-\rangle$：

$P(0)=\frac{1}{2},\quad P(1)=\frac{1}{2}$

因此，无论输入是 $|+\rangle$ 还是 $|-\rangle$，测量得到 0 和 1 的概率都一样。

所以：

**状态不同，并不代表任意一种测量都可以区分它们。**

必须选择合适的 measurement basis。

---

## 4. 如何完美区分 $|+\rangle$ 和 $|-\rangle$？

直接选择：

$\{|+\rangle,|-\rangle\}$

作为测量基。

如果输入是 $|+\rangle$，则一定测到 $+$。

如果输入是 $|-\rangle$，则一定测到 $-$。

因此：

**两个正交量子态可以被完美区分。**

成功率为：

$100\%$

第一个重要结论：

**正交态可以被完美区分。**

---

## 5. 更困难的情况：区分 $|0\rangle$ 和 $|+\rangle$

现在假设未知 qubit 只可能是：

$|0\rangle$ 或 $|+\rangle$

其中：

$|0\rangle=\begin{bmatrix}1\\0\end{bmatrix}$

而：

$|+\rangle=\frac{1}{\sqrt{2}}\begin{bmatrix}1\\1\end{bmatrix}$

在二维图中：

- $|0\rangle$：$0^\circ$
- $|+\rangle$：$45^\circ$

它们之间不是 $90^\circ$，所以不是正交态。

计算内积：

$\langle0|+\rangle=\frac{1}{\sqrt{2}}\neq0$

所以：

$|0\rangle\not\perp|+\rangle$

也就是说：

**$|0\rangle$ 和 $|+\rangle$ 不正交。**

---

## 6. 不正交意味着什么？

如果两个量子态满足：

$\langle\psi|\phi\rangle=0$

那么它们正交，可以被完美区分。

如果：

$\langle\psi|\phi\rangle\neq0$

那么它们不正交，不能通过一次测量做到 100% 正确区分。

所以可以记成：

- 正交 $\Rightarrow$ 可以完美区分
- 不正交 $\Rightarrow$ 不能完美区分

这里非常重要：

> 两个量子态虽然不同，并不代表一定可以通过一次测量 100% 判断出它们分别是谁。

例如：

$|0\rangle\neq|+\rangle$

但是：

$\langle0|+\rangle\neq0$

所以它们不能被完美区分。

---

## 7. 方法 1：使用 $0/1$ basis 测量

选择 computational basis：

$\{|0\rangle,|1\rangle\}$

规定：

- 测到 0 $\Rightarrow$ 猜原状态是 $|0\rangle$
- 测到 1 $\Rightarrow$ 猜原状态是 $|+\rangle$

### 情况 1：真实状态是 $|0\rangle$

如果输入状态是 $|0\rangle$，在 computational basis 下测量一定得到 0。

所以：

$P(\text{success}|0)=1$

也就是 100%。

### 情况 2：真实状态是 $|+\rangle$

因为：

$|+\rangle=\frac{1}{\sqrt{2}}|0\rangle+\frac{1}{\sqrt{2}}|1\rangle$

所以：

$P(0)=\frac{1}{2}$

$P(1)=\frac{1}{2}$

只有测到 1 时，我们才猜 $|+\rangle$。

因此：

$P(\text{success}|+)=\frac{1}{2}$

也就是 50%。

所以这种测量方法对两个候选态的成功率分别是：

$1$ 和 $\frac{1}{2}$

---

## 8. Average-case Success Probability

如果假设两个状态出现概率相同：

$P(|0\rangle)=P(|+\rangle)=\frac{1}{2}$

那么平均成功率为：

$P_{\text{avg}}=\frac{1}{2}\times1+\frac{1}{2}\times\frac{1}{2}=\frac{3}{4}$

因此：

$P_{\text{avg}}=75\%$

---

## 9. Worst-case Success Probability

两个状态对应的成功率分别是：

$1$ 和 $\frac{1}{2}$

worst-case 就是取较小值：

$P_{\text{worst}}=\frac{1}{2}=50\%$

---

## 10. 方法 2：使用 $+/-$ basis 测量

现在换一个测量基：

$\{|+\rangle,|-\rangle\}$

规定：

- $+$ $\Rightarrow$ 猜原状态是 $|+\rangle$
- $-$ $\Rightarrow$ 猜原状态是 $|0\rangle$

如果真实状态是 $|+\rangle$，则一定测到 $+$：

$P(\text{success}|+)=1$

如果真实状态是 $|0\rangle$：

$|0\rangle=\frac{1}{\sqrt{2}}|+\rangle+\frac{1}{\sqrt{2}}|-\rangle$

因此：

$P(+)=\frac{1}{2}$

$P(-)=\frac{1}{2}$

只有测到 $-$ 时才猜对，所以：

$P(\text{success}|0)=\frac{1}{2}$

因此：

$P_{\text{avg}}=\frac{3}{4}=75\%$

$P_{\text{worst}}=\frac{1}{2}=50\%$

---

## 11. 随机混合两种测量

可以规定：

- 50% 概率使用 $0/1$ basis
- 50% 概率使用 $+/-$ basis

对于输入 $|0\rangle$：

$P(\text{success}|0)=\frac{1}{2}\times1+\frac{1}{2}\times\frac{1}{2}=\frac{3}{4}$

对于输入 $|+\rangle$：

$P(\text{success}|+)=\frac{1}{2}\times\frac{1}{2}+\frac{1}{2}\times1=\frac{3}{4}$

所以：

$P_{\text{worst}}=75\%$

相比之前的 50% 更好。

---

## 12. 更优的测量方法

书中设计了一组新的 measurement basis：

$|\psi_0\rangle=\cos\left(\frac{\pi}{8}\right)|0\rangle-\sin\left(\frac{\pi}{8}\right)|1\rangle$

$|\psi_1\rangle=\sin\left(\frac{\pi}{8}\right)|0\rangle+\cos\left(\frac{\pi}{8}\right)|1\rangle$

因为：

$\frac{\pi}{8}=22.5^\circ$

所以：

- $|\psi_0\rangle$：$-22.5^\circ$
- $|\psi_1\rangle$：$67.5^\circ$
- $|0\rangle$：$0^\circ$
- $|+\rangle$：$45^\circ$

几何关系：

```text
                 |ψ1> 67.5°
                /
           |+> / 45°
              /
-------------→ |0> 0°
              \
               \
                |ψ0> -22.5°
