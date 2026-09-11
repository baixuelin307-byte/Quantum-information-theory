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

在当前二维示意图中，可以直接理解成二维坐标：

\[
|\psi\rangle \longleftrightarrow (\alpha,\beta)
\]

其中：

- \(|0\rangle\)：横轴方向
- \(|1\rangle\)：纵轴方向
- \(\alpha\)：横向分量
- \(\beta\)：纵向分量

因此：

\[
\boxed{\text{系数的正负决定方向，系数的大小决定偏向}}
\]

---

## 1. 根据正负判断方向

| \(\alpha\) | \(\beta\) | 方向 |
|---|---|---|
| 正 | 正 | 右上 ↗ |
| 正 | 负 | 右下 ↘ |
| 负 | 正 | 左上 ↖ |
| 负 | 负 | 左下 ↙ |

---

## 2. 例子：\(|+\rangle\)

\[
|+\rangle
=
\frac{1}{\sqrt2}|0\rangle
+
\frac{1}{\sqrt2}|1\rangle
\]

直接看两个系数：

\[
\alpha=\frac{1}{\sqrt2}>0
\]

\[
\beta=\frac{1}{\sqrt2}>0
\]

所以：

\[
(\alpha,\beta)=(+,+)
\]

因此方向是：

\[
\boxed{\text{右上 }\nearrow}
\]

写成列向量：

\[
|+\rangle
=
\frac{1}{\sqrt2}
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

直接看两个系数：

\[
\alpha=\frac{1}{\sqrt2}>0
\]

\[
\beta=-\frac{1}{\sqrt2}<0
\]

所以：

\[
(\alpha,\beta)=(+,-)
\]

因此方向是：

\[
\boxed{\text{右下 }\searrow}
\]

写成列向量：

\[
|-\rangle
=
\frac{1}{\sqrt2}
\begin{bmatrix}
1\\
-1
\end{bmatrix}
\]

---

## 4. 系数大小决定更靠近哪个轴

例如：

\[
|\psi\rangle
=
\frac{\sqrt3}{2}|0\rangle
+
\frac12|1\rangle
\]

两个系数都是正数，所以方向一定是右上。

但是：

\[
\frac{\sqrt3}{2}>\frac12
\]

因此 \(|0\rangle\) 的分量更大，所以这个状态更靠近横轴，也就是更偏向 \(|0\rangle\)。

反过来：

\[
|\psi\rangle
=
\frac12|0\rangle
+
\frac{\sqrt3}{2}|1\rangle
\]

仍然是右上方向，但更靠近纵轴，也就是更偏向 \(|1\rangle\)。

---

## 5. 快速判断方法

看到：

\[
|\psi\rangle=\alpha|0\rangle+\beta|1\rangle
\]

直接按下面的方法看：

1. \(|0\rangle\) 看成横轴；
2. \(|1\rangle\) 看成纵轴；
3. \(\alpha\) 的正负决定左右；
4. \(\beta\) 的正负决定上下；
5. 比较 \(|\alpha|\) 和 \(|\beta|\)，判断更靠近哪一个轴。

最简记忆：

\[
\boxed{
|\psi\rangle=\alpha|0\rangle+\beta|1\rangle
\longrightarrow
(\alpha,\beta)
}
\]

\[
\boxed{\text{正负决定方向，大小决定偏向}}
\]

---

## 6. 注意

不要只看状态名字中的 \(+\) 或 \(-\)。

真正需要看的是：

\[
|0\rangle
\]

和

\[
|1\rangle
\]

前面的系数。

例如：

\[
|-\rangle
=
\frac{1}{\sqrt2}|0\rangle
-
\frac{1}{\sqrt2}|1\rangle
\]

这里的负号表示的是：

\[
|1\rangle
\]

这个方向上的分量为负，所以整体方向指向右下。

> 该判断方法主要适用于当前讨论的实系数二维向量情况。若系数中出现 \(i\) 等复数，需要进一步考虑相位。
