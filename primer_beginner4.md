# 4: Introduction to state distinguishing problems 量子态区分问题介绍

声明：当我们物理 bit 转化成为量子 bit 后，量子 bit 的状态就是量子态。但是量子态也会细分很多种状态。

## 1: EX

$|+\rangle = \frac{1}{\sqrt{2}}|0\rangle + \frac{1}{\sqrt{2}}|1\rangle$

$|-\rangle = \frac{1}{\sqrt{2}}|0\rangle - \frac{1}{\sqrt{2}}|1\rangle$

这个例子中只有 plus 和 minus state，这两个都是属于正交态，因为：

$\langle + | - \rangle = 0$

<img width="218" height="205" alt="image" src="https://github.com/user-attachments/assets/ec1b9ad3-c5fd-4dde-8204-226d64211570" />

在二维的横截面上面，不同的符号代表的方向：

- $|1\rangle$ 向上
- $|0\rangle$ 向右
- $|+\rangle$ 右上
- $|-\rangle$ 右下
# 额外解释：如何从量子态公式直接判断方向

对于单量子比特状态：

\[
|\psi\rangle=\alpha|0\rangle+\beta|1\rangle
\]

在当前这张二维示意图中，可以把它直接理解成二维坐标：

\[
|\psi\rangle
\longleftrightarrow
(\alpha,\beta)
\]

其中：

- \(|0\rangle\)：横轴方向
- \(|1\rangle\)：纵轴方向
- \(\alpha\)：决定横向分量
- \(\beta\)：决定纵向分量

因此，看到公式时可以直接通过两个系数的**正负和大小**判断方向。

---

## 1. 先看正负：决定位于哪个方向

| \(\alpha\) | \(\beta\) | 方向 |
|---|---|---|
| 正 | 正 | 右上 ↗ |
| 正 | 负 | 右下 ↘ |
| 负 | 正 | 左上 ↖ |
| 负 | 负 | 左下 ↙ |

也就是：

\[
\boxed{\text{系数的正负决定方向所在的象限}}
\]

---

## 2. 例子：\(|+\rangle\)

\[
|+\rangle
=
\frac{1}{\sqrt2}|0\rangle
+
\frac{1}{\sqrt2}|1\rangle
\]

直接看系数：

\[
\alpha=\frac1{\sqrt2}>0
\]

\[
\beta=\frac1{\sqrt2}>0
\]

所以：

\[
(+,+)
\]

因此方向为：

\[
\boxed{\text{右上 } \nearrow}
\]

也可以写成列向量：

\[
|+\rangle
=
\frac1{\sqrt2}
\begin{bmatrix}
1\\
1
\end{bmatrix}
\]

---

## 3. 例子：\(|-\rangle\)

\[
|-\rangle
=
\frac{1}{\sqrt2}|0\rangle
-
\frac{1}{\sqrt2}|1\rangle
\]

直接看系数：

\[
\alpha=\frac1{\sqrt2}>0
\]

\[
\beta=-\frac1{\sqrt2}<0
\]

所以：

\[
(+,-)
\]

因此方向为：

\[
\boxed{\text{右下 } \searrow}
\]

写成列向量就是：

\[
|-\rangle
=
\frac1{\sqrt2}
\begin{bmatrix}
1\\
-1
\end{bmatrix}
\]

---

## 4. 系数大小决定更靠近哪个方向

除了看正负，还要看两个系数的绝对值大小。

例如：

\[
|\psi\rangle
=
\frac{\sqrt3}{2}|0\rangle
+
\frac12|1\rangle
\]

因为两个系数都是正数，所以一定在右上方向。

但是：

\[
\frac{\sqrt3}{2}>\frac12
\]

说明 \(|0\rangle\) 的分量更大，因此这个状态更偏向 \(|0\rangle\) 方向，也就是更靠近横轴。

即：

\[
\boxed{\text{更偏右，而不是更偏上}}
\]

反过来：

\[
|\psi\rangle
=
\frac12|0\rangle
+
\frac{\sqrt3}{2}|1\rangle
\]

仍然位于右上方向，但是因为 \(|1\rangle\) 的系数更大，所以更靠近纵轴。

---

## 5. 最简单的判断方法

看到

\[
|\psi\rangle=\alpha|0\rangle+\beta|1\rangle
\]

时，可以直接按下面的顺序判断：

1. 把 \(|0\rangle\) 看成横轴；
2. 把 \(|1\rangle\) 看成纵轴；
3. 看 \(\alpha\) 的正负，判断向左还是向右；
4. 看 \(\beta\) 的正负，判断向上还是向下；
5. 比较 \(|\alpha|\) 和 \(|\beta|\)，判断更靠近哪一个轴。

因此可以记成一句话：

\[
\boxed{
\text{正负决定方向，大小决定偏向}
}
\]

或者更完整地说：

\[
\boxed{
|\psi\rangle=\alpha|0\rangle+\beta|1\rangle
\quad\Longrightarrow\quad
(\alpha,\beta)
}
\]

---

## 6. 注意：这里的“+、−”是系数的符号

例如：

\[
|-\rangle
=
\frac1{\sqrt2}|0\rangle
-
\frac1{\sqrt2}|1\rangle
\]

这里的负号表示：

\[
|1\rangle
\]

这一方向上的分量是负的。

它并不是说：

> “这个量子态整体是负方向。”

因此不要只看状态名字中的 `+` 或 `-`。

真正应该看的是：

\[
\boxed{\text{\(|0\rangle\) 和 \(|1\rangle\) 前面的系数}}
\]

---

> **快速记忆**
>
> \[
> |0\rangle \rightarrow x\text{轴}
> \]
>
> \[
> |1\rangle \rightarrow y\text{轴}
> \]
>
> \[
> \alpha|0\rangle+\beta|1\rangle
> \rightarrow
> (\alpha,\beta)
> \]
>
> **正负决定象限，绝对值大小决定靠近哪条轴。**

> 注：这一判断方法适用于当前讨论的**实系数二维向量示意图**。如果后面量子态系数出现复数，例如 \(i/\sqrt2\)，就不能再只通过“上下左右”来表示，需要进一步考虑相位和 Bloch sphere。
