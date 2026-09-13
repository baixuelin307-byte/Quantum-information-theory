# 6.9 Controlled-NOT Gate（CNOT）

## 1. 什么是 CNOT

CNOT 全称是：

**Controlled-NOT Gate**

它是上一节 Controlled-U 的一个特殊情况。

当：

```math
U=X
```

也就是 U 取 NOT gate / Pauli-X gate 时：

```math
\text{Controlled-}U
=
\text{Controlled-}X
=
\text{CNOT}
```

电路表示：

```text
control ──●──
          │
target  ──X──
```

基本规则：

```text
control = 0
→ target 不变

control = 1
→ target 反转
```

这里的反转是：

```math
0\leftrightarrow1
```

---

## 2. CNOT 对 basis states 的作用

两个 qubits 的 computational basis：

```math
|00\rangle,\quad
|01\rangle,\quad
|10\rangle,\quad
|11\rangle
```

CNOT 的作用：

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

原因：

- 前两个状态 control = 0，所以 target 不变
- 后两个状态 control = 1，所以 target 反转

---

## 3. CNOT 与 XOR

假设：

- control = \(a\)
- target = \(b\)

那么 CNOT 可以写成：

```math
(a,b)
\rightarrow
(a,a\oplus b)
```

其中：

```math
\oplus
```

表示 XOR。

XOR 真值表：

| control \(a\) | target \(b\) | \(a\oplus b\) |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

因此：

```math
0\oplus b=b
```

所以 control = 0 时，target 不变。

而：

```math
1\oplus0=1
```

```math
1\oplus1=0
```

所以 control = 1 时，target 反转。

因此最重要的公式是：

```math
\boxed{
(a,b)\rightarrow(a,a\oplus b)
}
```

---

## 4. CNOT 的矩阵

CNOT 是一个 2-qubit gate，所以矩阵大小是：

```math
4\times4
```

其矩阵为：

```math
\mathrm{CNOT}
=
\begin{bmatrix}
1&0&0&0\\
0&1&0&0\\
0&0&0&1\\
0&0&1&0
\end{bmatrix}
```

它对应：

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

---

## 5. CNOT 对 superposition 同样有效

CNOT 不只可以作用于 basis states，也可以作用于 superposition。

例如：

```math
|+\rangle
=
\frac{|0\rangle+|1\rangle}{\sqrt{2}}
```

输入：

```math
|+\rangle|0\rangle
```

展开：

```math
|+\rangle|0\rangle
=
\frac{|00\rangle+|10\rangle}{\sqrt{2}}
```

其中：

```math
+
```

表示两个 basis states 的 **superposition**，不是 XOR。

经过 CNOT：

```math
|00\rangle\rightarrow|00\rangle
```

```math
|10\rangle\rightarrow|11\rangle
```

因此：

```math
|+\rangle|0\rangle
\rightarrow
\frac{|00\rangle+|11\rangle}{\sqrt{2}}
```

---

## 6. Superposition 和 Entanglement

输入：

```math
|+\rangle|0\rangle
```

虽然第一个 qubit 是 superposition，但整个状态仍然可以写成：

```math
|+\rangle\otimes|0\rangle
```

所以它是 **separable state（可分态）**。

也就是说：

```math
\frac{|00\rangle+|10\rangle}{\sqrt{2}}
=
\left(
\frac{|0\rangle+|1\rangle}{\sqrt{2}}
\right)
\otimes|0\rangle
```

它仍然可以拆成两个独立 qubit。

经过 CNOT 后：

```math
\frac{|00\rangle+|11\rangle}{\sqrt{2}}
```

这个状态不能写成：

```math
|\psi_1\rangle\otimes|\psi_2\rangle
```

所以它是：

**entangled state（纠缠态）**

因此：

```text
能写成 tensor product
→ separable

不能写成 tensor product
→ entangled
```

注意：

> superposition 不等于 entanglement。

一个 qubit 自己就可以处于 superposition。

Entanglement 是多个 qubits 之间的联合状态无法拆开。

---

## 7. 为什么 CNOT 可以产生 Entanglement

关键不只是“control 会影响 target”。

例如：

```math
|1\rangle|0\rangle
\rightarrow
|1\rangle|1\rangle
```

最后仍然是：

```math
|1\rangle\otimes|1\rangle
```

所以没有纠缠。

但如果 control 本身处于 superposition：

```math
\frac{|0\rangle+|1\rangle}{\sqrt{2}}
```

那么不同 control 分量会使 target 发生不同变化：

```text
control = 0
→ target 不变

control = 1
→ target 反转
```

于是：

```math
\frac{|00\rangle+|10\rangle}{\sqrt{2}}
\rightarrow
\frac{|00\rangle+|11\rangle}{\sqrt{2}}
```

最终两个 qubits 无法再分开描述。

可以简单记为：

```text
superposition control
+
conditional operation
→ 可能产生 entanglement
```

---

## 8. CNOT 可以用于构造更复杂的 Controlled-U

CNOT 是量子电路中非常基础的 2-qubit gate。

复杂的 controlled-U gate 可以通过：

```text
single-qubit gates
+
CNOT gates
```

组合实现。

也就是说：

```text
复杂量子门
→ 分解成基础量子门
```

这叫做 quantum circuit decomposition。

---

# 9. 最终记忆版

```text
CNOT = Controlled-X

control = 0
→ target 不变

control = 1
→ target 反转
```

数学表达：

```math
\boxed{
(a,b)\rightarrow(a,a\oplus b)
}
```

对 superposition：

```math
|+\rangle|0\rangle
=
\frac{|00\rangle+|10\rangle}{\sqrt{2}}
```

经过 CNOT：

```math
\boxed{
\frac{|00\rangle+|10\rangle}{\sqrt{2}}
\rightarrow
\frac{|00\rangle+|11\rangle}{\sqrt{2}}
}
```

前者可以写成 tensor product，是 **separable state**。

后者不能写成 tensor product，是 **entangled state**。
