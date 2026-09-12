4.1 State Distinguishing

1. 什么是 State Distinguishing？

State distinguishing（量子态区分）研究的是：

已知一个未知 qubit 来自若干候选量子态之一，如何通过测量判断它原来到底是哪一个状态。

基本流程可以理解为：

\text{给一个未知量子态}
\rightarrow
\text{知道它来自几个候选态}
\rightarrow
\text{选择测量基}
\rightarrow
\text{根据测量结果猜原状态}

2. 最简单的情况：区分 $|+\rangle$ 和 $|-\rangle$

定义：

|+\rangle
=
\frac{1}{\sqrt{2}}|0\rangle
+
\frac{1}{\sqrt{2}}|1\rangle

|-\rangle
=
\frac{1}{\sqrt{2}}|0\rangle
-
\frac{1}{\sqrt{2}}|1\rangle

写成二维向量：

|+\rangle
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
1
\end{bmatrix}

|-\rangle
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
-1
\end{bmatrix}

因此在二维图中：

$|+\rangle$：右上方向

$|-\rangle$：右下方向

计算内积：

\langle +|-\rangle = 0

所以：

|+\rangle \perp |-\rangle

也就是说，$|+\rangle$ 和 $|-\rangle$ 是正交态。

3. 为什么直接测量 $0/1$ 不能区分 $|+\rangle$ 和 $|-\rangle$？

如果使用 computational basis：

\{|0\rangle,|1\rangle\}

测量 $|+\rangle$：

P(0)=\frac{1}{2},
\qquad
P(1)=\frac{1}{2}

测量 $|-\rangle$：

P(0)=\frac{1}{2},
\qquad
P(1)=\frac{1}{2}

因此，无论输入是 $|+\rangle$ 还是 $|-\rangle$，测量得到 0 和 1 的概率都一样。

\text{状态不同，并不代表任意一种测量都可以区分它们}

必须选择合适的 measurement basis。

4. 如何完美区分 $|+\rangle$ 和 $|-\rangle$？

直接选择：

\{|+\rangle,|-\rangle\}

作为测量基。

如果输入是 $|+\rangle$，则一定测到 $+$。

如果输入是 $|-\rangle$，则一定测到 $-$。

因此：

\text{两个正交量子态可以被完美区分}

成功率为：

100\%

5. 更困难的情况：区分 $|0\rangle$ 和 $|+\rangle$

现在假设未知 qubit 只可能是：

|0\rangle \text{ 或 } |+\rangle

其中：

|0\rangle
=
\begin{bmatrix}
1 \\
0
\end{bmatrix}

而：

|+\rangle
=
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
1
\end{bmatrix}

在二维图中：

|0\rangle : 0^\circ

|+\rangle : 45^\circ

它们之间不是 $90^\circ$，因此不是正交态。

计算内积：

\langle 0|+\rangle
=
\frac{1}{\sqrt{2}}
\neq 0

所以：

|0\rangle \text{ 和 } |+\rangle \text{ 不正交}

6. 不正交意味着什么？

如果两个量子态满足：

\langle \psi|\phi\rangle = 0

那么它们正交，可以被完美区分。

如果：

\langle \psi|\phi\rangle \neq 0

那么它们不正交，不能通过一次测量做到 100% 正确区分。

\text{正交}
\Rightarrow
\text{可以完美区分}

\text{不正交}
\Rightarrow
\text{不能完美区分}

7. 方法 1：使用 $0/1$ basis 测量

选择 measurement basis：

\{|0\rangle,|1\rangle\}

规定：

\text{测到 }0
\Rightarrow
\text{猜原状态是 }|0\rangle

\text{测到 }1
\Rightarrow
\text{猜原状态是 }|+\rangle

如果真实状态是 $|0\rangle$：

P(\text{success}|0)=1

如果真实状态是 $|+\rangle$：

P(\text{success}|+)=\frac{1}{2}

若两个候选态出现概率相同，则平均成功率为：

P_{\mathrm{avg}}
=
\frac{1}{2}(1)
+
\frac{1}{2}\left(\frac{1}{2}\right)
=
\frac{3}{4}

因此：

P_{\mathrm{avg}}=75\%

最坏情况成功率为：

P_{\mathrm{worst}}=50\%

8. 方法 2：使用 $+/-$ basis 测量

选择：

\{|+\rangle,|-\rangle\}

规定：

+
\Rightarrow
\text{猜 }|+\rangle

-
\Rightarrow
\text{猜 }|0\rangle

于是：

P(\text{success}|+)=1

P(\text{success}|0)=\frac{1}{2}

所以：

P_{\mathrm{avg}}=\frac{3}{4}

P_{\mathrm{worst}}=\frac{1}{2}

9. 随机混合两种测量

可以规定：

50% 概率使用 $0/1$ basis；

50% 概率使用 $+/-$ basis。

对于输入 $|0\rangle$：

P(\text{success}|0)
=
\frac{1}{2}(1)
+
\frac{1}{2}\left(\frac{1}{2}\right)
=
\frac{3}{4}

对于输入 $|+\rangle$：

P(\text{success}|+)
=
\frac{1}{2}\left(\frac{1}{2}\right)
+
\frac{1}{2}(1)
=
\frac{3}{4}

因此：

P_{\mathrm{worst}}=75\%

10. 更优的测量方法

设计新的测量基：

|\psi_0\rangle
=
\cos\left(\frac{\pi}{8}\right)|0\rangle
-
\sin\left(\frac{\pi}{8}\right)|1\rangle

|\psi_1\rangle
=
\sin\left(\frac{\pi}{8}\right)|0\rangle
+
\cos\left(\frac{\pi}{8}\right)|1\rangle

其中：

\frac{\pi}{8}=22.5^\circ

对应方向：

|\psi_0\rangle:-22.5^\circ

|\psi_1\rangle:67.5^\circ

而：

|0\rangle:0^\circ

|+\rangle:45^\circ

几何关系：

                 |ψ1> 67.5°
                /
           |+> / 45°
              /
-------------→ |0> 0°
              \
               \
                |ψ0> -22.5°

并且：

67.5^\circ-(-22.5^\circ)=90^\circ

所以：

|\psi_0\rangle\perp|\psi_1\rangle

它们可以作为一组合法的 projective measurement basis。

规定：

\psi_0
\Rightarrow
\text{猜原状态是 }|0\rangle

\psi_1
\Rightarrow
\text{猜原状态是 }|+\rangle

成功率：

P(\psi_0|0)
=
|\langle\psi_0|0\rangle|^2
=
\cos^2\left(\frac{\pi}{8}\right)

P(\psi_1|+)
=
|\langle\psi_1|+\rangle|^2
=
\cos^2\left(\frac{\pi}{8}\right)

数值为：

\cos^2\left(\frac{\pi}{8}\right)
\approx 0.8536

即：

P_{\mathrm{success}}
\approx 85.36\%

11. 4.1 的核心逻辑

\text{未知量子态}
\rightarrow
\text{候选状态集合}
\rightarrow
\text{选择 measurement basis}
\rightarrow
\text{得到 measurement outcome}
\rightarrow
\text{判断原状态}

情况 1：候选态正交

例如：

|0\rangle,\ |1\rangle

或者：

|+\rangle,\ |-\rangle

满足：

\langle\psi|\phi\rangle=0

因此：

\text{正交态}
\Rightarrow
100\%\text{ 可以区分}

情况 2：候选态不正交

例如：

|0\rangle,\ |+\rangle

满足：

\langle0|+\rangle
=
\frac{1}{\sqrt{2}}
\neq0

因此：

\text{不正交态}
\Rightarrow
\text{不能 }100\%\text{ 区分}

只能通过设计更好的 measurement strategy 提高判断成功率。

对于 $|0\rangle$ 和 $|+\rangle$：

P_{\mathrm{optimal}}
=
\cos^2\left(\frac{\pi}{8}\right)
\approx85.36\%

12. 和通信系统的对应关系

State distinguishing 可以类比为通信系统中的接收端 detection：

\text{发送量子态}
\rightarrow
\text{接收未知量子态}
\rightarrow
\text{measurement}
\rightarrow
\text{decision}

例如发送端规定：

0\rightarrow|\phi_0\rangle

1\rightarrow|\phi_1\rangle

接收端拿到未知状态以后，通过 measurement 判断：

\hat{x}=0

或者：

\hat{x}=1

因此：

State distinguishing 本质上可以理解为量子通信接收端的 detection / decision 问题。
