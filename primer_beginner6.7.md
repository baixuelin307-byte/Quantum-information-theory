# 6.7 Multiplicative Property of Tensors

## 1. 和前面内容的关系

前面已经看到，在多 qubit 系统中，不同 subsystem 上的 local operations 可以用 tensor product 组合。

例如：

```text
Subsystem A → V
Subsystem B → U
```

整体操作可以写成：

```text
V ⊗ U
```

如果每个 subsystem 上又连续执行多个 operations，就会出现：

```text
(V2 ⊗ U2)(V1 ⊗ U1)
```

6.7 这一节就是说明：**这种 tensor product 形式的矩阵乘法可以直接拆开计算。**

---

## 2. Tensor Product 的乘法性质

核心公式是：

```text
(A ⊗ B)(C ⊗ D)
=
(AC) ⊗ (BD)
```

前提是：

```text
AC 可以正常做矩阵乘法
BD 可以正常做矩阵乘法
```

也就是说，矩阵维度必须匹配。

这个性质叫：

```text
multiplicative property of tensors
```

---

## 3. 怎么理解这个公式

可以把：

```text
A ⊗ B
```

看成分别作用在两个 subsystem 上的操作。

同样：

```text
C ⊗ D
```

也是分别作用在两个 subsystem 上。

那么：

```text
(A ⊗ B)(C ⊗ D)
```

就可以分别计算：

```text
第一个 subsystem：
C → A
最终 = AC

第二个 subsystem：
D → B
最终 = BD
```

所以整体结果就是：

```text
(AC) ⊗ (BD)
```

---

## 4. 在 Local Unitary Operations 中的应用

例如：

```text
Subsystem 1:
V1 → V2

Subsystem 2:
U1 → U2
```

按整个系统写：

```text
(V2 ⊗ U2)(V1 ⊗ U1)
```

利用 6.7 的乘法性质：

```text
(V2 ⊗ U2)(V1 ⊗ U1)
=
(V2V1) ⊗ (U2U1)
```

也就是说：

```text
Subsystem 1 → V2V1
Subsystem 2 → U2U1
```

最后再通过 tensor product 组合即可。

因此：

> **可以先分别计算每个 subsystem 内部的演化，再把结果 tensor product 起来。**

---

## 5. 书中的证明思路

书中使用 identity matrix 把 tensor product 拆开：

```text
A ⊗ B
=
(A ⊗ I)(I ⊗ B)
```

以及：

```text
C ⊗ D
=
(C ⊗ I)(I ⊗ D)
```

因此：

```text
(A ⊗ B)(C ⊗ D)
```

可以写成：

```text
(A ⊗ I)(I ⊗ B)(C ⊗ I)(I ⊗ D)
```

由于作用在不同 tensor factors 上的 operations 可以交换：

```text
(I ⊗ B)(C ⊗ I)
=
(C ⊗ I)(I ⊗ B)
```

所以可以整理成：

```text
(AC ⊗ I)(I ⊗ BD)
```

最终得到：

```text
(AC) ⊗ (BD)
```

---

## 6. 核心总结

```text
Tensor Product Multiplication
│
├── 核心公式
│   (A ⊗ B)(C ⊗ D)
│   =
│   (AC) ⊗ (BD)
│
├── 第一个 subsystem
│   └── C → A → AC
│
├── 第二个 subsystem
│   └── D → B → BD
│
└── 应用于 quantum circuit
    (V2 ⊗ U2)(V1 ⊗ U1)
    =
    (V2V1) ⊗ (U2U1)
```

最重要的一句话：

> **Tensor product 形式的矩阵相乘时，可以让各 subsystem 对应位置上的矩阵分别相乘，再把结果做 tensor product。**
