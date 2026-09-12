6.4 Product States

1. 什么是 Tensor Product（张量积）

在多 qubit 系统中，如果我们要把两个 subsystem 的状态组合成一个更大的整体系统，就使用：

tensor product

符号为：

⊗

可以把它理解成：

把两个子系统“组装”成一个联合量子系统。

例如：

|0⟩ ⊗ |1⟩ = |01⟩

这里：

|0⟩ = 第一个 qubit 的状态
|1⟩ = 第二个 qubit 的状态

通过 tensor product 组合后，得到 two-qubit system：

|01⟩

2. Tensor Product 的向量形式

单个 qubit：

|0⟩ = [1
       0]

|1⟩ = [0
       1]

那么：

|0⟩ ⊗ |1⟩

就是：

[1]   [0]
[0] ⊗ [1]

计算后得到：

[0
 1
 0
 0]

这就是：

|01⟩

所以：

2-dimensional
      ⊗
2-dimensional
      ↓
4-dimensional

三个 qubit 则是：

2 × 2 × 2 = 8-dimensional

一般来说：

n qubits → 2^n-dimensional state vector

3. 一般形式

假设第一个 qubit：

|ψ⟩ = α0|0⟩ + α1|1⟩

第二个 qubit：

|φ⟩ = β0|0⟩ + β1|1⟩

两个 qubit 的联合状态为：

|ψ⟩ ⊗ |φ⟩

展开：

(α0|0⟩ + α1|1⟩)
⊗
(β0|0⟩ + β1|1⟩)

得到：

α0β0|00⟩
+ α0β1|01⟩
+ α1β0|10⟩
+ α1β1|11⟩

对应 state vector：

[α0β0
 α0β1
 α1β0
 α1β1]

4. 什么是 Product State

如果一个多 qubit 状态可以写成多个 subsystem state 的 tensor product：

|ψ⟩ ⊗ |φ⟩

那么这个状态叫：

product state

例如：

|0⟩ ⊗ |1⟩ = |01⟩

所以：

|01⟩

是一个 product state。

它可以反过来拆成：

|01⟩ = |0⟩ ⊗ |1⟩

因此可以把 product state 理解成：

可以拆成各个 subsystem 独立状态的多 qubit state。

5. “组装”和“拆开”

Product state 可以理解成：

subsystem 1
     ⊗
subsystem 2
     ↓
whole system

例如：

|0⟩
 ⊗
|1⟩
 ↓
|01⟩

这是“组装”。

反过来：

|01⟩
 ↓
|0⟩ ⊗ |1⟩

这是“拆开”。

所以：

如果一个整体量子态可以拆成若干 subsystem states 的 tensor product，它就是 product state。

6. Computational Basis 的 Tensor Product

两个 qubit 的 computational basis 可以由单 qubit basis tensor product 得到。

|00⟩

|00⟩
= |0⟩ ⊗ |0⟩

对应：

[1
 0
 0
 0]

|01⟩

|01⟩
= |0⟩ ⊗ |1⟩

对应：

[0
 1
 0
 0]

|10⟩

|10⟩
= |1⟩ ⊗ |0⟩

对应：

[0
 0
 1
 0]

|11⟩

|11⟩
= |1⟩ ⊗ |1⟩

对应：

[0
 0
 0
 1]

因此：

|00⟩, |01⟩, |10⟩, |11⟩

构成 two-qubit system 的 computational basis。

7. Tensor Product 和 Kronecker Product

在量子信息中，我们通常说：

tensor product

在具体矩阵计算时，对应的是：

Kronecker product

假设：

A = [a11  a12
     a21  a22]

那么：

A ⊗ B

定义为：

[a11B  a12B
 a21B  a22B]

所以可以理解为：

Tensor Product
= 量子系统组合的概念

Kronecker Product
= 具体矩阵计算方式

8. 并不是所有多 qubit state 都是 Product State

这是这一节后面非常重要的一点。

例如：

(|00⟩ + |11⟩) / √2

这个状态不能写成：

|ψ⟩ ⊗ |φ⟩

因此它不是 product state。

这种不能拆成 subsystem tensor product 的状态叫：

entangled state

所以：

Product State
= 可以拆

Entangled State
= 不能拆

9. 和前面 Subsystem 的关系

前面讲 subsystem 时，是：

whole system
    ↓
只关注其中一部分
    ↓
subsystem

这一节刚好是反过来：

subsystem 1
      +
subsystem 2
      ↓
tensor product
      ↓
whole system

因此：

Subsystem
→ 把整体系统分开看

Tensor Product
→ 把多个 subsystem 组合起来

10. 核心总结

Tensor Product (⊗)
│
├── 用于组合 quantum subsystems
│
├── |0⟩ ⊗ |1⟩ = |01⟩
│
├── 维度相乘
│   └── 2 × 2 = 4
│
├── 多个 subsystem tensor product
│   └── 得到 whole quantum system
│
├── 如果整体 state 可以拆成 tensor product
│   └── Product State
│
└── 如果不能拆
    └── Entangled State

最重要的几句话：

1. Tensor product 是把两个 quantum subsystems 组合成一个更大系统的运算。

2. |0⟩ ⊗ |1⟩ = |01⟩，可以理解为把两个单 qubit 状态“组装”成一个 two-qubit state。

3. 如果一个多 qubit state 可以拆成若干 subsystem states 的 tensor product，那么它就是 product state。

4. Product state 可以拆；entangled state 不能拆。

5. n 个 qubits 的整体 state vector 维度是 2^n。
