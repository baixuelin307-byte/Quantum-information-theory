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

---

## 3. 为什么直接测量 $0/1$ 不能区分 $|+\rangle$ 和 $|-\rangle$？

如果使用 computational basis：

$$
\{|0\rangle,|1\rangle\}
$$

测量 $|+\rangle$：

$$
P(0)=\frac{1}{2},
\qquad
P(1)=\frac{1}{2}
$$

测量 $|-\rangle$：

$$
P(0)=\frac{1}{2},
\qquad
P(1)=\frac{1}{2}
$$

因此，无论输入是 $|+\rangle$ 还是 $|-\rangle$，测量得到 0 和 1 的概率都一样。

所以：

$$
\text{状态不同，并不代表任意一种测量都可以区分它们}
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

则一定测到：

$$
+
$$

如果输入是：

$$
|-\rangle
$$

则一定测到：

$$
-
$$

因此：

$$
\text{两个正交量子态可以被完美区分}
$$

成功率为：

$$
100\%
$$

所以第一个重要结论是：

$$
\boxed{
\text{正交态可以被完美区分}
}
$$

---

# 5. 更困难的情况：区分 $|0\rangle$ 和 $|+\rangle$

现在假设未知 qubit 只可能是：

$$
|0\rangle
\quad \text{或} \quad
|+\rangle
$$

其中：

$$
|0\rangle
=
\begin{bmatrix}
1 \\
0
\end{bmatrix}
$$

而：

$$
|+\rangle
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
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

也就是说：

- $|0\rangle$：向右
- $|+\rangle$：右上
- 两个方向之间夹角为 $45^\circ$

它们之间不是 $90^\circ$，所以不是正交态。

计算内积：

$$
\langle 0|+\rangle
=
\frac{1}{\sqrt{2}}
\neq 0
$$

因此：

$$
|0\rangle
\not\perp
|+\rangle
$$

也就是说：

$$
\boxed{
|0\rangle \text{ 和 } |+\rangle \text{ 不正交}
}
$$

---

## 6. 不正交意味着什么？

如果两个量子态满足：

$$
\langle \psi|\phi\rangle=0
$$

那么两个状态正交，可以被完美区分。

如果：

$$
\langle \psi|\phi\rangle\neq0
$$

那么两个状态不正交，不能通过一次测量做到 100% 正确区分。

所以可以记成：

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

这里非常重要：

> 两个量子态虽然不同，并不代表一定可以通过一次测量 100% 判断出它们分别是谁。

例如：

$$
|0\rangle \neq |+\rangle
$$

但是：

$$
\langle 0|+\rangle\neq0
$$

所以它们不能被完美区分。

---

# 7. 方法 1：使用 $0/1$ basis 测量

选择 computational basis：

$$
\{|0\rangle,|1\rangle\}
$$

然后规定：

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

## 情况 1：真实状态是 $|0\rangle$

如果输入状态是：

$$
|0\rangle
$$

在 computational basis 下测量一定得到：

$$
0
$$

因此：

$$
P(\text{success}|0)=1
$$

也就是：

$$
100\%
$$

---

## 情况 2：真实状态是 $|+\rangle$

因为：

$$
|+\rangle
=
\frac{1}{\sqrt{2}}|0\rangle
+
\frac{1}{\sqrt{2}}|1\rangle
$$

所以：

$$
P(0)=\frac{1}{2}
$$

$$
P(1)=\frac{1}{2}
$$

而我们的规则是：

$$
1
\Rightarrow
\text{猜 }|+\rangle
$$

所以只有测到 1 时才判断正确。

因此：

$$
P(\text{success}|+)
=
\frac{1}{2}
$$

也就是：

$$
50\%
$$

所以这种测量方法对两个候选态的成功率分别是：

$$
1
\qquad
\text{和}
\qquad
\frac{1}{2}
$$

---

## 8. Average-case Success Probability

如果假设两个状态出现概率相同：

$$
P(|0\rangle)
=
P(|+\rangle)
=
\frac{1}{2}
$$

那么平均成功率为：

$$
P_{\text{avg}}
=
\frac{1}{2}\times1
+
\frac{1}{2}\times\frac{1}{2}
$$

因此：

$$
P_{\text{avg}}
=
\frac{1}{2}
+
\frac{1}{4}
$$

所以：

$$
P_{\text{avg}}
=
\frac{3}{4}
$$

即：

$$
\boxed{
P_{\text{avg}}=75\%
}
$$

---

## 9. Worst-case Success Probability

两个状态对应的成功率分别是：

$$
1
\qquad
\text{和}
\qquad
\frac{1}{2}
$$

worst-case 就是取较小的那个：

$$
P_{\text{worst}}
=
\min
\left(
1,\frac{1}{2}
\right)
$$

因此：

$$
\boxed{
P_{\text{worst}}
=
\frac{1}{2}
=
50\%
}
$$

---

# 10. 方法 2：使用 $+/-$ basis 测量

现在换一个测量基：

$$
\{|+\rangle,|-\rangle\}
$$

规定：

$$
+
\Rightarrow
\text{猜原状态是 }|+\rangle
$$

$$
-
\Rightarrow
\text{猜原状态是 }|0\rangle
$$

---

## 如果真实状态是 $|+\rangle$

因为测量基本身包含：

$$
|+\rangle
$$

所以一定测到：

$$
+
$$

因此：

$$
P(\text{success}|+)=1
$$

---

## 如果真实状态是 $|0\rangle$

可以写成：

$$
|0\rangle
=
\frac{1}{\sqrt{2}}|+\rangle
+
\frac{1}{\sqrt{2}}|-\rangle
$$

因此：

$$
P(+)=\frac{1}{2}
$$

$$
P(-)=\frac{1}{2}
$$

只有测到 $-$ 时，我们才猜：

$$
|0\rangle
$$

所以：

$$
P(\text{success}|0)
=
\frac{1}{2}
$$

于是：

$$
P(\text{success}|+)=1
$$

$$
P(\text{success}|0)=\frac{1}{2}
$$

和方法 1 刚好反过来。

平均成功率仍然是：

$$
P_{\text{avg}}
=
\frac{3}{4}
=
75\%
$$

最坏情况成功率仍然是：

$$
P_{\text{worst}}
=
\frac{1}{2}
=
50\%
$$

---

# 11. 随机混合两种测量

现在进一步改进。

我们规定：

- 50% 概率使用 $0/1$ basis
- 50% 概率使用 $+/-$ basis

---

## 对于输入 $|0\rangle$

第一种测量成功率是：

$$
1
$$

第二种测量成功率是：

$$
\frac{1}{2}
$$

所以：

$$
P(\text{success}|0)
=
\frac{1}{2}\times1
+
\frac{1}{2}\times\frac{1}{2}
$$

因此：

$$
P(\text{success}|0)
=
\frac{3}{4}
$$

---

## 对于输入 $|+\rangle$

第一种测量成功率是：

$$
\frac{1}{2}
$$

第二种测量成功率是：

$$
1
$$

所以：

$$
P(\text{success}|+)
=
\frac{1}{2}\times\frac{1}{2}
+
\frac{1}{2}\times1
$$

因此：

$$
P(\text{success}|+)
=
\frac{3}{4}
$$

所以现在两个状态的成功率都是：

$$
75\%
$$

因此：

$$
\boxed{
P_{\text{worst}}
=
75\%
}
$$

相比之前的：

$$
50\%
$$

已经提高了。

---

# 12. 但是还能做得更好

书中设计了一组新的 measurement basis：

$$
|\psi_0\rangle
=
\cos\left(\frac{\pi}{8}\right)|0\rangle
-
\sin\left(\frac{\pi}{8}\right)|1\rangle
$$

$$
|\psi_1\rangle
=
\sin\left(\frac{\pi}{8}\right)|0\rangle
+
\cos\left(\frac{\pi}{8}\right)|1\rangle
$$

因为：

$$
\frac{\pi}{8}
=
22.5^\circ
$$

所以：

$$
|\psi_0\rangle
:
-22.5^\circ
$$

$$
|\psi_1\rangle
:
67.5^\circ
$$

而原来的两个候选态：

$$
|0\rangle
:
0^\circ
$$

$$
|+\rangle
:
45^\circ
$$

所以几何关系可以理解为：

```text
                 |ψ1> 67.5°
                /
           |+> / 45°
              /
-------------→ |0> 0°
              \
               \
                |ψ0> -22.5°
```

---

## 13. 为什么 $|\psi_0\rangle$ 和 $|\psi_1\rangle$ 可以作为测量基？

因为：

$$
67.5^\circ
-
(-22.5^\circ)
=
90^\circ
$$

所以：

$$
|\psi_0\rangle
\perp
|\psi_1\rangle
$$

也就是说：

$$
\langle\psi_0|\psi_1\rangle=0
$$

因此：

$$
\boxed{
|\psi_0\rangle,\ |\psi_1\rangle
\text{ 是一组正交测量基}
}
$$

---

# 14. 如何用这组测量基区分 $|0\rangle$ 和 $|+\rangle$？

规定：

$$
\psi_0
\Rightarrow
\text{猜原状态是 }|0\rangle
$$

$$
\psi_1
\Rightarrow
\text{猜原状态是 }|+\rangle
$$

注意：

$$
|0\rangle
$$

和：

$$
|\psi_0\rangle
$$

只相差：

$$
22.5^\circ
$$

因此测到 $\psi_0$ 的概率很高：

$$
P(\psi_0|0)
=
|\langle\psi_0|0\rangle|^2
$$

计算：

$$
P(\psi_0|0)
=
\cos^2\left(\frac{\pi}{8}\right)
$$

同样：

$$
|+\rangle
$$

和：

$$
|\psi_1\rangle
$$

也只相差：

$$
22.5^\circ
$$

因此：

$$
P(\psi_1|+)
=
|\langle\psi_1|+\rangle|^2
$$

得到：

$$
P(\psi_1|+)
=
\cos^2\left(\frac{\pi}{8}\right)
$$

而：

$$
\cos^2\left(\frac{\pi}{8}\right)
\approx
0.8536
$$

所以：

$$
\boxed{
P_{\text{success}}
\approx
85.36\%
}
$$

这比：

$$
75\%
$$

更高。

---

# 15. 为什么测量结果和候选状态不是同一个东西？

这里非常容易混淆。

我们真正想区分的候选态是：

$$
|0\rangle
\quad
\text{和}
\quad
|+\rangle
$$

但是我们使用的测量基是：

$$
|\psi_0\rangle
\quad
\text{和}
\quad
|\psi_1\rangle
$$

所以：

- $|0\rangle$、$|+\rangle$：是我们想判断的原始状态
- $|\psi_0\rangle$、$|\psi_1\rangle$：是测量使用的两个方向

规定：

$$
\psi_0
\Rightarrow
\text{猜 }|0\rangle
$$

$$
\psi_1
\Rightarrow
\text{猜 }|+\rangle
$$

例如真实状态是：

$$
|0\rangle
$$

但是测量结果可能得到：

$$
\psi_1
$$

这时候根据判决规则，我们会猜：

$$
|+\rangle
$$

于是就发生错误。

所以：

$$
\boxed{
\text{测量结果}
\neq
\text{原始候选状态}
}
$$

测量结果只是我们进行判断的依据。

---

# 16. 4.1 的核心逻辑

整个 4.1 可以总结成：

$$
\text{未知量子态}
\rightarrow
\text{已知候选状态集合}
\rightarrow
\text{选择 measurement basis}
\rightarrow
\text{得到 measurement outcome}
\rightarrow
\text{根据结果判断原状态}
$$

---

## 情况 1：候选态正交

例如：

$$
|0\rangle,\ |1\rangle
$$

或者：

$$
|+\rangle,\ |-\rangle
$$

满足：

$$
\langle\psi|\phi\rangle=0
$$

因此：

$$
\boxed{
\text{正交态}
\Rightarrow
100\%
\text{ 可以区分}
}
$$

---

## 情况 2：候选态不正交

例如：

$$
|0\rangle,\ |+\rangle
$$

因为：

$$
\langle0|+\rangle
=
\frac{1}{\sqrt{2}}
\neq0
$$

所以：

$$
\boxed{
\text{不正交态}
\Rightarrow
\text{不能 }100\%
\text{ 区分}
}
$$

只能通过设计更好的 measurement strategy 提高判断成功率。

对于：

$$
|0\rangle
\quad
\text{和}
\quad
|+\rangle
$$

最优成功率为：

$$
\boxed{
P_{\text{optimal}}
=
\cos^2\left(\frac{\pi}{8}\right)
\approx
85.36\%
}
$$

---

# 17. 和通信系统的对应关系

State distinguishing 可以理解成量子通信接收端的 detection / decision。

例如发送端规定：

$$
0
\rightarrow
|\phi_0\rangle
$$

$$
1
\rightarrow
|\phi_1\rangle
$$

发送以后：

$$
\text{发送量子态}
\rightarrow
\text{经过信道}
\rightarrow
\text{接收量子态}
\rightarrow
\text{measurement}
\rightarrow
\text{decision}
$$

接收端需要判断：

$$
\hat{x}=0
$$

或者：

$$
\hat{x}=1
$$

因此：

> **State distinguishing 本质上可以理解为量子通信接收端的 detection / decision 问题。**

---

# 18. 最重要的结论

### 结论 1

量子态可以有很多种，不只是：

$$
|0\rangle
\quad
\text{和}
\quad
|1\rangle
$$

例如：

$$
|+\rangle
$$

$$
|-\rangle
$$

以及：

$$
|\psi\rangle
=
\alpha|0\rangle
+
\beta|1\rangle
$$

都是合法量子态。

---

### 结论 2

测量之前必须确定使用什么 measurement basis。

不同 measurement basis 会产生不同的测量结果概率。

---

### 结论 3

两个状态如果正交：

$$
\langle\psi|\phi\rangle=0
$$

则：

$$
\boxed{
\text{可以 }100\%\text{ 完美区分}
}
$$

---

### 结论 4

两个状态如果不正交：

$$
\langle\psi|\phi\rangle\neq0
$$

则：

$$
\boxed{
\text{不能通过一次测量 }100\%\text{ 区分}
}
$$

---

### 结论 5

不正交并不代表完全无法判断。

可以设计更好的 measurement basis，提高成功概率。

例如：

$$
|0\rangle
\quad
\text{和}
\quad
|+\rangle
$$

最优成功率为：

$$
\boxed{
\cos^2\left(\frac{\pi}{8}\right)
\approx
85.36\%
}
$$

---

# 19. 一句话总结 4.1

> **State distinguishing 就是：已知一个未知量子态来自几个候选态之一，通过设计合适的量子测量，尽可能准确地判断它原来是哪一个状态。**

最核心的判断规则：

$$
\boxed{
\langle\psi|\phi\rangle=0
\Rightarrow
\text{可以完美区分}
}
$$

$$
\boxed{
\langle\psi|\phi\rangle\neq0
\Rightarrow
\text{不能完美区分，需要优化测量}
}
$$
