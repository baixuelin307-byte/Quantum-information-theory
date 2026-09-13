# 6.8 Controlled-\(U\) Gates

## 1. 什么是 Controlled-\(U\) Gate

Controlled-\(U\) gate 是一种两量子比特门。

其中：

- 第一个 qubit：**control qubit**
- 第二个 qubit：**target qubit**

它的基本规则是：

$$
\text{control}=|0\rangle
\Rightarrow
\text{target 不发生变化}
$$

$$
\text{control}=|1\rangle
\Rightarrow
\text{对 target 执行 }U
$$

这里的重点是：

> control qubit 本身通常不变，它只负责决定 target 是否执行 \(U\)。

---

## 2. “对 target 执行 \(U\)”是什么意思

“对 target 执行 \(U\)”不是默认把 target 反转。

它的意思是：

> target 按照量子门 \(U\) 的规则发生变化。

例如：

### 当 \(U=X\)

$$
X|0\rangle=|1\rangle
$$

$$
X|1\rangle=|0\rangle
$$

这时候 target 会发生反转。

因此：

$$
\text{Controlled-}X=\text{CNOT}
$$

### 当 \(U=Z\)

$$
Z|0\rangle=|0\rangle
$$

$$
Z|1\rangle=-|1\rangle
$$

这时候不是反转，而是改变 phase。

### 当 \(U=H\)

$$
H|0\rangle
=
\frac{|0\rangle+|1\rangle}{\sqrt{2}}
$$
这时候 target 会进入 superposition。

因此：

$$
\boxed{
\text{control 决定“做不做”，target 是真正被操作的 qubit}
}
$$

---

## 3. Controlled-\(U\) 的电路表示

```text
control   ──●──
            │
target    ──U──
```

其中：

- `●` 表示 control qubit
- `U` 表示作用在 target qubit 上的量子门

---

## 4. 两量子比特的 Computational Basis

对于两个 qubits，basis states 是：

$$
|00\rangle,\quad
|01\rangle,\quad
|10\rangle,\quad
|11\rangle
$$

其中：

$$
|ab\rangle
$$

可以理解为：

- 第一个 qubit \(a\)：control
- 第二个 qubit \(b\)：target

---

## 5. 当 Control = 0

如果 control 是 \(0\)，那么什么都不做。

因此：

$$
|00\rangle \rightarrow |00\rangle
$$

$$
|01\rangle \rightarrow |01\rangle
$$

target 保持不变。

---

## 6. 当 Control = 1

如果 control 是 \(1\)，那么对 target 执行 \(U\)。

设：

$$
U=
\begin{bmatrix}
u_{00} & u_{01}\\
u_{10} & u_{11}
\end{bmatrix}
$$

那么：

$$
U|0\rangle
=
u_{00}|0\rangle
+
u_{10}|1\rangle
$$

因此：

$$
|10\rangle
\rightarrow
u_{00}|10\rangle
+
u_{10}|11\rangle
$$

同理：

$$
U|1\rangle
=
u_{01}|0\rangle
+
u_{11}|1\rangle
$$

因此：

$$
|11\rangle
\rightarrow
u_{01}|10\rangle
+
u_{11}|11\rangle
$$

所以完整变化关系是：

$$
\begin{aligned}
|00\rangle &\rightarrow |00\rangle\\
|01\rangle &\rightarrow |01\rangle\\
|10\rangle &\rightarrow u_{00}|10\rangle+u_{10}|11\rangle\\
|11\rangle &\rightarrow u_{01}|10\rangle+u_{11}|11\rangle
\end{aligned}
$$

---

## 7. Controlled-\(U\) 的矩阵

因为 Controlled-\(U\) 是一个 2-qubit gate，所以其矩阵大小是：

$$
2^2 \times 2^2 = 4 \times 4
$$

其矩阵形式为：

$$
CU=
\begin{bmatrix}
1&0&0&0\\
0&1&0&0\\
0&0&u_{00}&u_{01}\\
0&0&u_{10}&u_{11}
\end{bmatrix}
$$

也可以写成 block matrix：

$$
CU=
\begin{bmatrix}
I&0\\
0&U
\end{bmatrix}
$$

其中：

$$
I=
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix}
$$

原因是：

- control = 0 时，执行 \(I\)
- control = 1 时，执行 \(U\)

---

## 8. 最重要的公式

Controlled-\(U\) 可以概括为：

$$
|0\rangle|\psi\rangle
\rightarrow
|0\rangle|\psi\rangle
$$

$$
|1\rangle|\psi\rangle
\rightarrow
|1\rangle U|\psi\rangle
$$

也就是：

$$
\boxed{
\text{control}=0 \Rightarrow \text{target 不变}
}
$$

$$
\boxed{
\text{control}=1 \Rightarrow \text{target 执行 }U
}
$$

---

## 9. 经典例子：CNOT

如果：

$$
U=X
$$

那么 Controlled-\(U\) 就变成：

$$
\text{Controlled-}X=\text{CNOT}
$$

其变化为：

$$
|00\rangle\rightarrow|00\rangle
$$

$$
|01\rangle\rightarrow|01\rangle
$$

$$
|10\rangle\rightarrow|11\rangle
$$

$$
|11\rangle\rightarrow|10\rangle
$$

这里可以看出：

- control qubit 没有变化
- 只有当 control = 1 时
- target 才被 \(X\) gate 反转

---

## 10. 最终记忆版

```text
control = 0
→ target 不动

control = 1
→ target 执行 U
```

注意：

> \(U\) 不一定是反转。

只有：

$$
U=X
$$

时，target 才会发生：

$$
0\leftrightarrow1
$$

所以：

$$
\boxed{
\text{control 负责判断，target 负责执行}
}
$$
