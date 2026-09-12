
4.1 ：如果别人给你一个未知 qubit，它只可能来自几个候选状态之一，我们怎么通过测量判断它到底是哪一个状态。
       state distinguishing
       # 4.1 State Distinguishing

## 1. 什么是 State Distinguishing？

State distinguishing（量子态区分）研究的是：

> 已知一个未知 qubit 来自若干候选量子态之一，如何通过测量判断它原来到底是哪一个状态。

基本流程可以理解为：

$$
\boxed{
\text{给一个未知量子态}
\rightarrow
\text{知道它来自几个候选态}
\rightarrow
\text{选择测量基}
\rightarrow
\text{根据测量结果猜原状态}
}
$$

---

## 2. 最简单的情况：区分 $|+\rangle$ 和 $|-\rangle$

定义：

$$
|+\rangle
=
\frac{1}{\sqrt2}|0\rangle
+
\frac{1}{\sqrt2}|1\rangle
$$

$$
|-\rangle
=
\frac{1}{\sqrt2}|0\rangle
-
\frac{1}{\sqrt2}|1\rangle
$$

写成二维向量：

$$
|+\rangle
=
\frac1{\sqrt2}
\begin{bmatrix}
1\\
1
\end{bmatrix}
$$

$$
|-\rangle
=
\frac1{\sqrt2}
\begin{bmatrix}
1\\
-1
\end{bmatrix}
$$

因此在二维图中：

- $|+\rangle$：右上方向
- $|-\rangle$：右下方向

计算它们的内积：

$$
\langle +|-\rangle = 0
$$

因此：

$$
\boxed{|+\rangle \perp |-\rangle}
$$

也就是说，$|+\rangle$ 和 $|-\rangle$ 是正交态。

---

## 3. 为什么直接测量 $0/1$ 不能区分 $|+\rangle$ 和 $|-\rangle$？

如果使用 computational basis：

$$
\{|0\rangle,|1\rangle\}
$$

测量 $|+\rangle$：

$$
P(0)=\frac12,
\qquad
P(1)=\frac12
$$

测量 $|-\rangle$：

$$
P(0)=\frac12,
\qquad
P(1)=\frac12
$$

因此无论输入是 $|+\rangle$ 还是 $|-\rangle$，测量得到 $0$ 和 $1$ 的概率都一样。

所以：

$$
\boxed{
\text{状态不同，并不代表任意一种测量都可以区分它们}
}
$$

必须选择合适的 measurement basis。

---

## 4. 如何完美区分 $|+\rangle$ 和 $|-\rangle$？

直接选择：

$$
\{|+\rangle,|-\rangle\}
$$

作为测量基。

如果输入是：

$$
|+\rangle
$$

则一定测到 $+$。

如果输入是：

$$
|-\rangle
$$

则一定测到 $-$。

因此：

$$
\boxed{
\text{两个正交量子态可以被完美区分}
}
$$

成功率为：

$$
\boxed{100\%}
$$

---

# 5. 更困难的情况：区分 $|0\rangle$ 和 $|+\rangle$

现在假设未知 qubit 只可能是：

$$
\boxed{|0\rangle \text{ 或 } |+\rangle}
$$

其中：

$$
|0\rangle
=
\begin{bmatrix}
1\\
0
\end{bmatrix}
$$

而：

$$
|+\rangle
=
\frac1{\sqrt2}
\begin{bmatrix}
1\\
1
\end{bmatrix}
$$

在二维图中：

$$
|0\rangle : 0^\circ
$$

$$
|+\rangle : 45^\circ
$$

它们之间不是 $90^\circ$，因此不是正交态。

计算内积：

$$
\langle 0|+\rangle
=
\frac1{\sqrt2}
\neq 0
$$

所以：

$$
\boxed{
|0\rangle \text{ 和 } |+\rangle \text{ 不正交}
}
$$

---

## 6. 不正交意味着什么？

如果两个量子态满足：

$$
\langle\psi|\phi\rangle=0
$$

那么它们正交，可以被完美区分。

如果：

$$
\langle\psi|\phi\rangle\neq0
$$

那么它们不正交，不能通过一次测量做到 $100\%$ 正确区分。

因此：

$$
\boxed{
\text{正交}
\Rightarrow
\text{可以完美区分}
}
$$

$$
\boxed{
\text{不正交}
\Rightarrow
\text{不能完美区分}
}
$$

这也是量子信息中的一个重要特点：

> 不同的量子态，并不一定可以被完全区分。

---

# 7. 方法 1：使用 $0/1$ basis 测量

选择 measurement basis：

$$
\{|0\rangle,|1\rangle\}
$$

规定：

$$
\text{测到 }0
\Rightarrow
\text{猜原状态是 }|0\rangle
$$

$$
\text{测到 }1
\Rightarrow
\text{猜原状态是 }|+\rangle
$$

---

## 输入为 $|0\rangle$

如果真实状态是：

$$
|0\rangle
$$

那么 computational basis 测量一定得到：

$$
0
$$

因此：

$$
P(\text{success}|0)=1
$$

---

## 输入为 $|+\rangle$

因为：

$$
|+\rangle
=
\frac{|0\rangle+|1\rangle}{\sqrt2}
$$

所以：

$$
P(0)=\frac12
$$

$$
P(1)=\frac12
$$

只有测到 $1$ 时，我们才会猜 $|+\rangle$。

因此：

$$
P(\text{success}|+)=\frac12
$$

所以两种输入对应的成功率分别为：

$$
1,
\qquad
\frac12
$$

---

## Average-case Success Probability

如果假设两个候选态出现概率相同：

$$
P(|0\rangle)=P(|+\rangle)=\frac12
$$

那么平均成功率为：

$$
P_{\text{avg}}
=
\frac12(1)
+
\frac12\left(\frac12\right)
$$

$$
=
\frac34
$$

因此：

$$
\boxed{
P_{\text{avg}}=75\%
}
$$

---

## Worst-case Success Probability

两个状态的成功率是：

$$
1,
\qquad
\frac12
$$

取其中较小值：

$$
\boxed{
P_{\text{worst}}=\frac12=50\%
}
$$

---

# 8. 方法 2：使用 $+/-$ basis 测量

选择：

$$
\{|+\rangle,|-\rangle\}
$$

作为测量基。

规定：

$$
+\Rightarrow\text{猜 }|+\rangle
$$

$$
-\Rightarrow\text{猜 }|0\rangle
$$

如果真实状态是 $|+\rangle$：

$$
P(\text{success}|+)=1
$$

如果真实状态是 $|0\rangle$：

$$
|0\rangle
=
\frac1{\sqrt2}|+\rangle
+
\frac1{\sqrt2}|-\rangle
$$

因此：

$$
P(+)=\frac12,
\qquad
P(-)=\frac12
$$

只有得到 $-$ 时才猜对，因此：

$$
P(\text{success}|0)=\frac12
$$

所以：

$$
P_{\text{avg}}=\frac34
$$

$$
P_{\text{worst}}=\frac12
$$

和方法 1 一样，只是两个状态的成功率交换了。

---

# 9. 随机混合两种测量

可以进一步规定：

- $50\%$ 概率使用 $0/1$ basis
- $50\%$ 概率使用 $+/-$ basis

对于输入 $|0\rangle$：

$$
P(\text{success}|0)
=
\frac12(1)
+
\frac12\left(\frac12\right)
$$

$$
=
\frac34
$$

对于输入 $|+\rangle$：

$$
P(\text{success}|+)
=
\frac12\left(\frac12\right)
+
\frac12(1)
$$

$$
=
\frac34
$$

因此两个状态的成功率都变成：

$$
\boxed{75\%}
$$

于是：

$$
\boxed{
P_{\text{worst}}=75\%
}
$$

相比之前的 $50\%$ 更好。

---

# 10. 更优的测量方法

还可以设计一组新的测量基：

$$
|\psi_0\rangle
=
\cos\frac{\pi}{8}|0\rangle
-
\sin\frac{\pi}{8}|1\rangle
$$

$$
|\psi_1\rangle
=
\sin\frac{\pi}{8}|0\rangle
+
\cos\frac{\pi}{8}|1\rangle
$$

因为：

$$
\frac{\pi}{8}=22.5^\circ
$$

所以：

$$
|\psi_0\rangle:-22.5^\circ
$$

$$
|\psi_1\rangle:67.5^\circ
$$

而：

$$
|0\rangle:0^\circ
$$

$$
|+\rangle:45^\circ
$$

几何关系可以表示为：

```text
                 |ψ1> 67.5°
                /
           |+> / 45°
              /
-------------→ |0> 0°
              \
               \
                |ψ0> -22.5°


      
