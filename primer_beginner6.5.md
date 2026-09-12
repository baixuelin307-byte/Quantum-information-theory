# 6.5 Notation for Explicitly Referring to Individual Qubits

## 1. 为什么需要给 Qubit 加标签

在多 qubit 系统中，如果只写：

```text
|0⟩
|1⟩
|00⟩
|01⟩
```

当 qubit 数量增加时，很容易不知道某个 ket 到底对应哪一个 qubit。

因此可以给 qubit 加下标，例如：

```text
|0⟩₁
|1⟩₂
|0⟩₃
```

分别表示：

```text
|0⟩₁ = 第 1 个 qubit 处于 |0⟩
|1⟩₂ = 第 2 个 qubit 处于 |1⟩
|0⟩₃ = 第 3 个 qubit 处于 |0⟩
```

---

## 2. Qubit Label 只是标签，不代表物理位置

书中强调：

> qubit 的编号只是为了区分不同 qubit，并不表示它们在现实空间中的物理位置。

例如：

```text
1   2   3
```

和：

```text
3   1   2
```

只是不同的书写或标记方式。

所以：

```text
qubit label ≠ physical location
```

下标 `1,2,3` 只是名字。

---

## 3. 有了标签之后，可以改变书写顺序

例如：

```text
|1⟩₁ |0⟩₂ |1⟩₃
```

表示：

```text
qubit 1 → |1⟩
qubit 2 → |0⟩
qubit 3 → |1⟩
```

因为每个 ket 都有明确的下标，所以即使改变书写顺序，也不会产生歧义：

```text
|1⟩₃ |1⟩₁ |0⟩₂
```

仍然表示同样三个 qubit 的状态，只是书写顺序不同。

---

## 4. 对多个 Qubit 组成的 Subsystem 也可以加标签

例如：

```text
|00⟩₁,₃
```

表示：

```text
由 qubit 1 和 qubit 3 组成的 two-qubit state
```

同样：

```text
|11⟩₁,₃
```

表示 qubit 1 和 qubit 3 共同处于 `|11⟩`。

这样就可以明确表示：

```text
(|00⟩₁,₃ + |11⟩₁,₃) ⊗ |0⟩₂
```

意思是：

```text
qubit 1 和 qubit 3
→ 构成一个 two-qubit subsystem

qubit 2
→ 单独处于 |0⟩
```

---

## 5. 为什么这种写法很重要

如果只写：

```text
(|00⟩ + |11⟩) ⊗ |0⟩
```

虽然在简单情况下可以理解，但 qubit 数量增加后会产生歧义：

```text
|00⟩ 到底对应哪两个 qubits？
|0⟩ 又对应哪一个 qubit？
```

加入标签之后：

```text
(|00⟩₁,₃ + |11⟩₁,₃) ⊗ |0⟩₂
```

就非常清楚。

因此：

> **qubit label 的主要作用就是消除多 qubit 系统中的歧义。**

---

## 6. Alice 和 Bob 的 Qubit Label

在量子通信中，经常会有不同参与者分别持有多个 qubits。

例如：

```text
Alice → A1, A2
Bob   → B1, B2
```

这里：

```text
A1 = Alice 的第 1 个 qubit
A2 = Alice 的第 2 个 qubit

B1 = Bob 的第 1 个 qubit
B2 = Bob 的第 2 个 qubit
```

这种写法比统一编号：

```text
1, 2, 3, 4
```

更加直观。

---

## 7. Alice 和 Bob 的例子

假设 Alice 和 Bob 各有两个 qubits。

如果：

```text
A1 和 B1 是一对
A2 和 B2 是另一对
```

那么可以写成：

```text
(|00⟩A1,B1 + |11⟩A1,B1)
⊗
(|00⟩A2,B2 + |11⟩A2,B2)
```

这样可以非常明确地看出：

```text
第一对 subsystem → A1, B1
第二对 subsystem → A2, B2
```

不会混淆 Alice 和 Bob 手中的不同 qubits。

---

## 8. 展开 Tensor Product 时标签仍然保留

例如：

```text
(|00⟩A1,B1 + |11⟩A1,B1)
⊗
(|00⟩A2,B2 + |11⟩A2,B2)
```

展开后会得到四项：

```text
|00⟩A1,B1 |00⟩A2,B2
+
|00⟩A1,B1 |11⟩A2,B2
+
|11⟩A1,B1 |00⟩A2,B2
+
|11⟩A1,B1 |11⟩A2,B2
```

标签始终告诉我们：

```text
每个 ket 属于哪些 qubits
```

---

## 9. 和 6.4 Product States 的关系

6.4 主要讲：

```text
多个 subsystem
      ↓
tensor product
      ↓
组成 whole system
```

6.5 主要解决：

```text
多个 subsystem 很多时
      ↓
怎么明确指出
每个 ket 属于哪些 qubits
```

所以：

```text
6.4 → 怎么组合 subsystem
6.5 → 怎么给 subsystem / qubit 做明确标记
```

---

## 10. 核心总结

```text
Qubit Label
│
├── 用下标标记具体 qubit
│
│   |0⟩₁
│   |1⟩₂
│
├── 标签只是名字
│   └── 不代表物理位置
│
├── 可以改变书写顺序
│   └── 只要 label 清楚就不会歧义
│
├── 可以标记多个 qubits
│   └── |00⟩₁,₃
│
├── 量子通信中常用参与者标签
│   ├── A1, A2
│   └── B1, B2
│
└── 主要作用
    └── 消除多 qubit 系统中的歧义
```

最重要的几句话：

> **1. 给 qubit 加下标，是为了明确某个状态到底属于哪个 qubit。**

> **2. qubit label 只是数学标签，不代表真实的物理空间位置。**

> **3. 对多个 qubits 组成的 subsystem，也可以一起加标签，例如 `|00⟩₁,₃`。**

> **4. 在量子通信中，可以用 `A1, A2, B1, B2` 来区分 Alice 和 Bob 各自持有的 qubits。**

> **5. 6.5 的核心不是新的量子操作，而是建立一种不容易混淆的多 qubit 记号体系。**
