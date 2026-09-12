# 6.2 n-bit 系统的子系统（Subsystems of n-bit Systems）

## 1. 整体系统与子系统

一个 `n-bit system` 可以看成一个整体系统，也可以只关注其中的一部分 bit，把这一部分称为 **subsystem（子系统）**。

例如，一个 3-bit system 的所有可能状态为：

```text
000, 001, 010, 011,
100, 101, 110, 111
```

一共有：

```text
2^3 = 8
```

种 possible states。

因此，整个 3-bit system 可以用一个 8 维 probability vector 表示：

```text
[p000
 p001
 p010
 p011
 p100
 p101
 p110
 p111]
```

并且所有概率之和满足：

```text
p000 + p001 + p010 + p011
+ p100 + p101 + p110 + p111 = 1
```

---

## 2. 单独一个 bit 的状态

虽然整个系统由 3 个 bits 构成，但我们也可以只关注其中某一个 bit。

例如，只考虑第一个 bit。

第一个 bit 只有两种可能状态：

```text
0
1
```

第一个 bit 为 `0` 的概率为：

```text
P(first bit = 0)
= p000 + p001 + p010 + p011
```

因为这四个整体状态的第一位都是 `0`。

第一个 bit 为 `1` 的概率为：

```text
P(first bit = 1)
= p100 + p101 + p110 + p111
```

因此，第一个 bit 这个 subsystem 的 probability vector 为：

```text
[p000 + p001 + p010 + p011
 p100 + p101 + p110 + p111]
```

---

## 3. Marginalization（边缘化）

从整个系统得到 subsystem 状态的过程叫做：

```text
marginalization
```

核心思想是：

> 对于不关心的 bits，把它们对应的概率加起来。

例如只关注第一个 bit 时，第二个和第三个 bit 的具体取值不重要，因此把它们所有可能情况的概率求和。

可以理解为：

```text
Whole probability distribution
        ↓
只保留关心的 bit
        ↓
对其他 bits 的状态求和
        ↓
Subsystem probability distribution
```

因此，subsystem 的状态不是简单地从原始 probability vector 中截取几个元素，而是要对不关心的部分进行求和。

---

## 4. 任意 Subsystem

同样的方法可以用于任意 subsystem。

例如可以只考虑：

```text
第二个 bit
第三个 bit
前两个 bits
第一个和第三个 bit
```

只要把不属于该 subsystem 的 bits 对应的概率求和，就可以得到该 subsystem 的 probability distribution。

---

## 5. 对 Subsystem 进行操作

一个 operation 也可以只作用在系统中的某一个 subsystem 上。

例如，一个 operation `S` 只作用在第一个 bit：

```text
bit 1 → S
bit 2 → 不变
bit 3 → 不变
```

对于整个 3-bit system，可以写成：

```text
S ⊗ I ⊗ I
```

其中：

```text
S = 作用在第一个 bit 上的 operation
I = identity operation（恒等操作）
```

`I` 表示对应的 bit 不发生变化。

---

## 6. Local Operations

不同的 operation 可以作用在不同的 bits 上。

例如：

```text
S → 第一个 bit
T → 第二个 bit
U → 第三个 bit
```

这些都属于 **local operations（局部操作）**，因为每个 operation 只作用在某个 subsystem 上。

示意：

```text
3-bit system

bit 1 ── S ─────────
bit 2 ─────── T ────
bit 3 ─────────── U ─
```

需要注意：

```text
S、T、U 只是一般的 operation
```

它们不一定表示 bit flip。

bit flip 只是 operation 的一种，例如：

```text
0 → 1
1 → 0
```

---

## 7. 核心总结

```text
n-bit system
│
├── 整体系统
│   └── 用 2^n 维 probability vector 表示
│
├── Subsystem
│   └── 只关注其中一部分 bits
│
├── Subsystem state
│   └── 对其他 bits 做 marginalization
│       即把不关心的状态概率加起来
│
└── Local operation
    └── operation 可以只作用在某一个 subsystem
```

最重要的一点：

> **Subsystem 的状态不是从完整 probability vector 中直接截取，而是通过 marginalization，把不关心的 bits 对应的概率求和。**

例如，3-bit system 中只看第一个 bit：

```text
[p000
 p001
 p010
 p011
 p100
 p101
 p110
 p111]

↓

[p000 + p001 + p010 + p011
 p100 + p101 + p110 + p111]
```

这就是 6.2 `Subsystems of n-bit Systems` 的核心内容。
