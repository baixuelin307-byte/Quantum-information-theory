# 6.8 Controlled-U Gates

## 1. 什么是 Controlled-U Gate

Controlled-U gate 是一种两量子比特门。

其中：

- 第一个 qubit：**control qubit**
- 第二个 qubit：**target qubit**

基本规则：

```math
\text{control}=|0\rangle
\Rightarrow
\text{target 不发生变化}
```

```math
\text{control}=|1\rangle
\Rightarrow
\text{对 target 执行 }U
```

这里的重点是：

> control qubit 本身通常不变，它只负责决定 target 是否执行 U。

---

## 2. “对 target 执行 U”是什么意思

“对 target 执行 U”不是默认把 target 反转。

它的意思是：

> target 按照量子门 U 的规则发生变化。

### 当 U = X

```math
X|0\rangle=|1\rangle
```

```math
X|1\rangle=|0\rangle
```

这时候 target 会发生反转。

```math
\text{Controlled-}X=\text{CNOT}
```

### 当 U = Z

```math
Z|0\rangle=|0\rangle
```

```math
Z|1\rangle=-|1\rangle
```

这时候不是反转，而是改变 phase。

### 当 U = H

```math
H|0\rangle
=
\frac{|0\rangle+|1\rangle}{\sqrt{2}}
```

这时候 target 会进入 superposition。

```math
\boxed{
\text{control 决定“做不做”，target 是真正被操作的 qubit}
}
```

---

## 3. Controlled-U 的电路表示

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

```math
|00\rangle,\quad
|01\rangle,\quad
|10\rangle,\quad
|11\rangle
```

其中：

```math
|ab\rangle
```

可以理解为：

- 第一个 qubit a：control
- 第二个 qubit b：target

---

## 5. 当 Control = 0

如果 control 是 0，那么什么都不做。

```math
|00\rangle \rightarrow |00\rangle
```

```math
|01\rangle \rightarrow |01\rangle
```

target 保持不变。

---

## 6. 当 Control = 1

如果 control 是 1，那么对 target 执行 U。

设：

```math
U=
\begin{bmatrix}
u_{00} & u_{01}\\
u_{10} & u_{11}
\end{bmatrix}
```

那么：

```math
U|0\rangle
=
u_{00}|0\rangle
+
u_{10}|1\rangle
```

因此：

```math
|10\rangle
\rightarrow
u_{00}|10\rangle
+
u_{10}|11\rangle
```

同理：

```math
U|1\rangle
=
u_{01}|0\rangle
+
u_{11}|1\rangle
```

因此：

```math
|11\rangle
\rightarrow
u_{01}|10\rangle
+
u_{11}|11\rangle
```

完整变化关系：

```math
\begin{aligned}
|00\rangle &\rightarrow |00\rangle\\
|01\rangle &\rightarrow |01\rangle\\
|10\rangle &\rightarrow u_{00}|10\rangle+u_{10}|11\rangle\\
|11\rangle &\rightarrow u_{01}|10\rangle+u_{11}|11\rangle
\end{aligned}
```

---

## 7. Controlled-U 的矩阵

因为 Controlled-U 是一个 2-qubit gate，所以其矩阵大小是：

```math
2^2 \times 2^2 = 4 \times 4
```

其矩阵形式为：

```math
CU=
\begin{bmatrix}
1&0&0&0\\
0&1&0&0\\
0&0&u_{00}&u_{01}\\
0&0&u_{10}&u_{11}
\end{bmatrix}
```

也可以写成 block matrix：

```math
CU=
\begin{bmatrix}
I&0\\
0&U
\end{bmatrix}
```

其中：

```math
I=
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix}
```

原因是：

- control = 0 时，执行 I
- control = 1 时，执行 U

---

## 8. 最重要的公式

Controlled-U 可以概括为：

```math
|0\rangle|\psi\rangle
\rightarrow
|0\rangle|\psi\rangle
```

```math
|1\rangle|\psi\rangle
\rightarrow
|1\rangle U|\psi\rangle
```

也就是：

```math
\boxed{
\text{control}=0 \Rightarrow \text{target 不变}
}
```

```math
\boxed{
\text{control}=1 \Rightarrow \text{target 执行 }U
}
```

---

## 9. 经典例子：CNOT

如果 U = X，那么 Controlled-U 就变成 Controlled-X，也就是 CNOT。

```math
U=X
```

```math
\text{Controlled-}X=\text{CNOT}
```

其变化为：

```math
|00\rangle\rightarrow|00\rangle
```

```math
|01\rangle\rightarrow|01\rangle
```

```math
|10\rangle\rightarrow|11\rangle
```

```math
|11\rangle\rightarrow|10\rangle
```

这里可以看出：

- control qubit 没有变化
- 只有当 control = 1 时
- target 才被 X gate 反转

---

## 10. 最终记忆版

```text
control = 0
→ target 不动

control = 1
→ target 执行 U
```

注意：

> U 不一定是反转。

只有 U = X 时，target 才会发生：

```math
0\leftrightarrow1
```

所以：

```math
\boxed{
\text{control 负责判断，target 负责执行}
}
```

---

## 11. Controlled-U 对任意两量子比特状态都适用

Controlled-U 不只适用于 computational basis states。

任意 2-qubit state 都可以表示成一个 4 维向量，因此都可以直接乘以 Controlled-U 的 \(4\times4\) 矩阵。

也就是说，即使输入是 superposition 或 entangled state，Controlled-U 仍然正常定义。

例如：

```math
|\psi\rangle
=
a|00\rangle+b|01\rangle+c|10\rangle+d|11\rangle
```

Controlled-U 对整个状态的作用，就是：

```math
|\psi'\rangle
=
CU|\psi\rangle
```

---

## 12. Controlled-U 会不会改变 control qubit？

书里给了一个值得思考的问题：

> Controlled-U 是否可能改变 control qubit 的状态？

对于标准 Controlled-U：

- control = 0 时，对 target 什么都不做
- control = 1 时，对 target 执行 U
- **control 本身不直接被 U 操作**

因此在 computational basis 的直观理解里，control 只是决定 target 是否执行 U。

但是如果输入本身是 superposition，整个两量子比特系统可能形成 entanglement，所以不能只把它理解成两个完全独立的 classical bits。

---

## 13. Control 和 Target 可以交换位置

前面默认：

- 第一个 qubit = control
- 第二个 qubit = target

电路为：

```text
control   ──●──
            │
target    ──U──
```

也可以把方向反过来：

- 第一个 qubit = target
- 第二个 qubit = control

电路可以理解为：

```text
target    ──U──
            │
control   ──●──
```

这时：

> 第二个 qubit 决定是否对第一个 qubit 执行 U。

假设 basis 顺序仍然是：

```math
|00\rangle,\quad |01\rangle,\quad |10\rangle,\quad |11\rangle
```

由于第二个 qubit 是 control，因此：

```math
|00\rangle \rightarrow |00\rangle
```

```math
|10\rangle \rightarrow |10\rangle
```

而当第二个 qubit 为 1 时，对第一个 qubit 执行 U。

设：

```math
U=
\begin{bmatrix}
u_{00} & u_{01}\\
u_{10} & u_{11}
\end{bmatrix}
```

那么：

```math
|01\rangle
\rightarrow
u_{00}|01\rangle
+
u_{10}|11\rangle
```

```math
|11\rangle
\rightarrow
u_{01}|01\rangle
+
u_{11}|11\rangle
```

对应的矩阵为：

```math
CU_{\text{reversed}}
=
\begin{bmatrix}
1 & 0 & 0 & 0\\
0 & u_{00} & 0 & u_{01}\\
0 & 0 & 1 & 0\\
0 & u_{10} & 0 & u_{11}
\end{bmatrix}
```

所以：

> control 和 target 的位置可以交换，但矩阵形式也会随 qubit 顺序改变。

---

## 14. Controlled-U 可以推广到 n-qubit 的 U

Controlled-U 不要求 U 一定只是 1-qubit gate。

如果 U 本身是一个 n-qubit unitary gate，那么再增加一个 control qubit，就得到一个：

```math
(n+1)\text{-qubit controlled-}U
```

其基本规则仍然完全一样：

```math
\text{control}=0
\Rightarrow
\text{n 个 target qubits 不执行 }U
```

```math
\text{control}=1
\Rightarrow
\text{对 n 个 target qubits 执行 }U
```

如果 control qubit 放在最前面，那么矩阵仍然可以写成 block form：

```math
CU=
\begin{bmatrix}
I & 0\\
0 & U
\end{bmatrix}
```

其中：

- \(U\) 是 \(2^n\times2^n\) matrix
- \(I\) 也是 \(2^n\times2^n\) identity matrix
- 整个 Controlled-U 是 \(2^{n+1}\times2^{n+1}\) matrix

---

## 15. 这一页的核心总结

```text
1. Controlled-U 对所有 2-qubit states 都有效，
   不只对 |00>, |01>, |10>, |11> 有效。

2. control qubit 负责决定“是否执行 U”，
   U 真正作用的是 target。

3. control 和 target 的上下位置可以交换，
   但对应矩阵会改变。

4. U 不一定只是 1-qubit gate。
   如果 U 是 n-qubit gate，
   Controlled-U 就是 (n+1)-qubit gate。
```

最重要的思想仍然是：

```math
\boxed{
\text{control 决定是否执行，target 接受 }U\text{ 的作用}
}
```
