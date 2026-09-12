# 4.2 Global Phases

## 1. 什么是 Global Phase？

对于一个量子态：

$|\psi\rangle$

如果整个状态同时乘上一个复数相位：

$e^{i\theta}$

得到：

$e^{i\theta}|\psi\rangle$

那么这两个 state vector 在物理上被认为是同一个量子态。

也就是说：

$|\psi\rangle \sim e^{i\theta}|\psi\rangle$

其中：

$|e^{i\theta}|=1$

---

## 2. 例子：$|+\rangle$ 和 $-|+\rangle$

定义：

$|+\rangle=\frac{1}{\sqrt{2}}|0\rangle+\frac{1}{\sqrt{2}}|1\rangle$

整体乘上 $-1$：

$-|+\rangle=-\frac{1}{\sqrt{2}}|0\rangle-\frac{1}{\sqrt{2}}|1\rangle$

因为：

$-1=e^{i\pi}$

所以：

$-|+\rangle=e^{i\pi}|+\rangle$

因此 $|+\rangle$ 和 $-|+\rangle$ 只相差一个 global phase。

它们在物理上是同一个状态。

---

## 3. 为什么 Global Phase 不影响测量结果？

假设某个振幅是：

$\alpha$

乘上 global phase 后变成：

$e^{i\theta}\alpha$

测量概率取模平方：

$|e^{i\theta}\alpha|^2$

因为：

$|e^{i\theta}|^2=1$

所以：

$|e^{i\theta}\alpha|^2=|\alpha|^2$

因此：

**Global phase 不会改变任何测量概率。**

也就是说：

**Global phase 是不可观测的。**

---

## 4. Global Phase 和 Relative Phase 的区别

### Global Phase

例如：

$|+\rangle=\frac{1}{\sqrt{2}}|0\rangle+\frac{1}{\sqrt{2}}|1\rangle$

整体乘上 $-1$：

$-\frac{1}{\sqrt{2}}|0\rangle-\frac{1}{\sqrt{2}}|1\rangle$

两个分量一起变化。

这种变化叫：

**Global phase**

它不会改变物理状态。

---

### Relative Phase

如果只改变其中一个分量：

$\frac{1}{\sqrt{2}}|0\rangle+\frac{1}{\sqrt{2}}|1\rangle$

变成：

$\frac{1}{\sqrt{2}}|0\rangle-\frac{1}{\sqrt{2}}|1\rangle$

也就是：

$|+\rangle \rightarrow |-\rangle$

这里不是整个状态一起乘同一个相位，而是两个分量之间的相对关系发生了变化。

这种变化叫：

**Relative phase**

Relative phase 会改变物理状态。

---

## 5. 为什么 Relative Phase 会影响测量结果？

$|+\rangle$ 和 $|-\rangle$ 是两个不同的物理状态。

虽然在 computational basis：

$\{|0\rangle,|1\rangle\}$

下测量时，两者都是：

$P(0)=\frac{1}{2}$

$P(1)=\frac{1}{2}$

但是如果使用：

$\{|+\rangle,|-\rangle\}$

作为测量基：

- $|+\rangle$ 一定测到 $+$
- $|-\rangle$ 一定测到 $-$

所以 relative phase 的变化可以通过合适的测量被观察出来。

---

## 6. 和 State Distinguishing 的关系

在 state distinguishing 中：

Global phase 不会影响区分结果。

例如：

$|1\rangle$

和：

$-|1\rangle$

物理上是同一个状态。

因此在分析量子态区分问题时，可以忽略整体 global phase。

有些新的 state distinguishing 问题，也可以通过：

- 忽略 global phase
- 使用 unitary rotation

转化成之前已经解决过的问题。

---

## 7. 最重要的结论

1. $|\psi\rangle$ 和 $e^{i\theta}|\psi\rangle$ 表示同一个物理状态。

2. Global phase 不改变测量概率。

3. Global phase 是不可观测的。

4. Relative phase 会改变不同分量之间的关系。

5. Relative phase 可能改变物理状态。

6. Relative phase 可以影响干涉和测量结果。

---

## 一句话总结

**Global phase 不改变物理状态，也不会影响测量结果；Relative phase 会改变物理状态，因此可能影响测量结果。**
