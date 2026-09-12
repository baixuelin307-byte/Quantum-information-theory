# 3.1 Notation for Qubits and Higher-Dimensional Analogues
## Qubit 及更高维量子系统的符号表示

先回顾一下，一个 qubit 的状态可以写成概率幅向量：

$(\alpha_0,\alpha_1)$

其中：

$\alpha_0,\alpha_1\in\mathbb{C}$

并且满足归一化条件：

$|\alpha_0|^2+|\alpha_1|^2=1$

也就是说，这个向量是一个 unit vector（单位向量）。

---

## 1. Ket 是什么？

在量子信息中，我们通常不用普通列向量直接表示量子态，而使用：

$|\psi\rangle$

这种记法叫：

**bra-ket notation（狄拉克记号）**

其中：

$|\psi\rangle$

叫做一个：

**ket**

对于单个 qubit：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

它等价于概率幅向量：

$(\alpha_0,\alpha_1)$

其中：

$|0\rangle=(1,0)$

$|1\rangle=(0,1)$

因此：

$\alpha_0|0\rangle+\alpha_1|1\rangle$

就对应：

$(\alpha_0,\alpha_1)$

---

## 2. Computational Basis States

$|0\rangle$

和：

$|1\rangle$

叫做：

**computational basis states（计算基态）**

一个一般的 qubit：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

可以理解为 $|0\rangle$ 和 $|1\rangle$ 的 superposition（叠加）。

---

## 3. Higher-Dimensional Quantum Systems

如果不是 qubit，而是一个 $d$ 维量子系统，那么量子态可以写成：

$|\psi\rangle=(\alpha_0,\alpha_1,\ldots,\alpha_{d-1})$

其中：

$\alpha_j\in\mathbb{C}$

并且满足：

$|\alpha_0|^2+|\alpha_1|^2+\cdots+|\alpha_{d-1}|^2=1$

也就是说：

> 所有 probability amplitudes 的模平方加起来必须等于 1。

这些模平方对应测量得到各个 basis state 的概率。

---

## 4. Unnormalized State Notation

有时为了简化表达，我们会省略归一化常数。

例如：

$\frac{1}{\sqrt{2}}|0\rangle+\frac{1}{\sqrt{2}}|1\rangle$

有时可以简写为：

$|0\rangle+|1\rangle$

但这时要理解为：

> 这个向量还没有 normalized（归一化）。

如果一个非零向量写成：

$|\psi\rangle$

但没有归一化，那么真正对应的量子态应理解为：

$\frac{|\psi\rangle}{\|\,|\psi\rangle\,\|}$

也就是说：

**未归一化向量 ÷ 自身范数 = 合法量子态**

---

# 3.3 Unitary Operations
## 幺正操作

量子态的演化通常写成：

$|\psi'\rangle=U|\psi\rangle$

其中：

$U$

是 unitary matrix（幺正矩阵）。

---

## 1. Unitary Matrix 的核心性质

### 性质 1：保持内积不变

如果两个状态分别是：

$|\psi\rangle$

和：

$|\phi\rangle$

经过相同的 unitary transformation 后：

$U|\psi\rangle$

和：

$U|\phi\rangle$

它们之间的内积关系保持不变。

也就是说：

> unitary operation 不会改变两个量子态之间的几何关系。

---

### 性质 2：行和列都是 Orthonormal

幺正矩阵的行向量和列向量都是 orthonormal（正交归一）的。

也就是说：

- 每个向量长度为 1
- 不同向量之间的内积为 0

---

### 性质 3：满足

$U^\dagger U=I$

其中：

- $U^\dagger$：$U$ 的 conjugate transpose（共轭转置）
- $I$：identity matrix（单位矩阵）

因此：

$U^{-1}=U^\dagger$

也就是说，幺正操作是可逆的。

---

## 2. 常见的 Unitary Operations

常见的量子门包括：

- Hadamard gate $H$
- Pauli-X gate
- Pauli-Y gate
- Pauli-Z gate
- Rotation gate

---

### Pauli-X Gate

Pauli-X 类似 classical NOT operation：

$|0\rangle\leftrightarrow|1\rangle$

所以也叫：

**bit flip**

---

### Pauli-Z Gate

Pauli-Z 不交换 $|0\rangle$ 和 $|1\rangle$，而是改变相位：

$|0\rangle\rightarrow|0\rangle$

$|1\rangle\rightarrow-|1\rangle$

所以也叫：

**phase flip**

---

## 3. 核心理解

可以把 unitary operation 理解成：

> **把一个合法量子态变换成另一个合法量子态，同时保持向量长度和量子态之间的内积关系不变。**

一个简单的信息处理流程可以写成：

`classical information`

`→ encode into quantum state`

`→ unitary evolution U`

`→ probability amplitudes / phases change`

`→ information is transformed but not destroyed`

`→ measurement`

由于 unitary operation 是可逆的，所以在测量之前，信息原则上仍然可以通过逆操作恢复。

---

# 3.4 Understanding Quantum Measurement
## 更深入理解量子测量

假设一个 qubit 处于：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

并且：

$|\alpha_0|^2+|\alpha_1|^2=1$

其中：

- $\alpha_0$：对应 $|0\rangle$ 的 probability amplitude
- $\alpha_1$：对应 $|1\rangle$ 的 probability amplitude

---

## 1. 测量之前

在进行最终测量之前，量子算法通常会通过一系列 unitary operations 对量子态进行处理。

这些操作会改变：

- probability amplitudes
- relative phases
- interference pattern

目标通常是：

> **让我们想要的答案在最终测量时具有更高的概率出现。**

---

## 2. Computational Basis Measurement

如果最后使用 computational basis：

$\{|0\rangle,|1\rangle\}$

进行测量，那么：

测量得到 0 的概率是：

$P(0)=|\alpha_0|^2$

并且测量后状态变成：

$|0\rangle$

测量得到 1 的概率是：

$P(1)=|\alpha_1|^2$

并且测量后状态变成：

$|1\rangle$

---

## 3. Measurement Collapse

因此：

如果结果是 0：

$|\psi\rangle\rightarrow|0\rangle$

如果结果是 1：

$|\psi\rangle\rightarrow|1\rangle$

这个过程通常叫：

**state collapse（量子态坍缩）**

---

## 4. Quantum Algorithm 的基本逻辑

整个流程可以理解为：

`input information`

`→ quantum state`

`→ unitary operations`

`→ change amplitudes and phases`

`→ interference`

`→ measurement`

`→ classical result`

也就是说：

> **量子算法不是简单地先把量子态“变成 0 或 1”，而是先通过量子操作调整概率幅和相位，让正确答案在最终测量时更容易被得到。**

---

## 5. 最重要的理解

量子计算的核心并不是：

`直接决定答案是 0 或 1`

而更像是：

`调整 probability amplitudes`

`+`

`调整 relative phases`

`+`

`利用 interference`

`↓`

`提高目标答案的 measurement probability`

最后通过 measurement 得到 classical result。

---

# 一句话总结

### Qubit Representation

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

### Unitary Evolution

$|\psi'\rangle=U|\psi\rangle$

### Measurement

$P(0)=|\alpha_0|^2$

$P(1)=|\alpha_1|^2$

### 整体流程

`quantum state → unitary evolution → interference → measurement → classical result`

> **量子态在测量前通过 unitary operation 改变概率幅和相位；最终测量时，根据概率幅的模平方得到 classical outcome。**



