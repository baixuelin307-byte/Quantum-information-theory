6.3 n-qubit 系统的子系统（Subsystems of n-qubit Systems）

1. n-qubit 系统也可以划分为子系统

和 classical n-bit system 类似，一个 n-qubit system 既可以看成一个整体，也可以只关注其中一部分 qubits。

例如，一个 3-qubit system 的状态可以写成：

[α000
 α001
 α010
 α011
 α100
 α101
 α110
 α111]

这里的：

α000, α001, ..., α111

不是概率，而是 probability amplitudes（概率幅）。

对应 basis state 的实际测量概率为：

P(ijk) = |αijk|²

2. 为什么不能像 classical bit 一样直接相加？

在 classical 3-bit system 中，如果只关心第一个 bit，可以直接把所有第一位相同的概率加起来：

P(b1 = 0)
= p000 + p001 + p010 + p011

因为：

p000, p001, ...

本身就是 probability。

但是在 quantum system 中：

α000, α001, ...

是 amplitude，不是 probability。

所以不能直接写成：

α000 + α001 + α010 + α011

来表示第一个 qubit 为 0 的概率。

3. 书中的反例

书中给出了一个 3-qubit state：

[ 1/√8
 -1/√8
  1/√8
 -1/√8
  1/√8
 -1/√8
  1/√8
 -1/√8 ]

如果错误地像 classical probability 一样，把前四个 amplitudes 相加：

1/√8 - 1/√8 + 1/√8 - 1/√8 = 0

后四个也得到：

0

于是会得到：

[0
 0]

这显然不是一个合法的 qubit state，因为：

|0|² + |0|² = 0 ≠ 1

因此：

quantum subsystem 不能通过“直接把 amplitudes 相加”得到。

4. 如果只想求测量概率分布

如果我们只想知道某个 subsystem 的 measurement probability distribution（测量概率分布），可以先对 amplitude 取模平方，再对不关心的 qubits 求和。

例如，对于 3-qubit system，只关心第一个 qubit：

P(q1 = 0)
= |α000|²
+ |α001|²
+ |α010|²
+ |α011|²

P(q1 = 1)
= |α100|²
+ |α101|²
+ |α110|²
+ |α111|²

因此流程是：

probability amplitude α
        ↓
取模平方 |α|²
        ↓
得到 basis state 的 probability
        ↓
对不关心的 qubits 求和
        ↓
得到 subsystem 的测量概率分布

也就是说：

如果只是求“测量时得到 0 或 1 的概率”，先取模平方，再求和即可。

5. 测量概率分布 ≠ 完整量子态

需要注意：

[P(q1 = 0),
 P(q1 = 1)]

只告诉我们：

测量 q1 时得到 0 或 1 的概率

它并不能完整表示这个 subsystem 的 quantum state。

因为完整量子态还可能包含：

phase
coherence
entanglement 带来的 mixed state

这些信息不能只靠 measurement probability distribution 表示。

6. 完整表示 Subsystem 的量子态

如果目标不是单纯求测量概率，而是要描述 subsystem 本身的完整 quantum state，就需要使用：

density matrix

并通过：

partial trace

把不关心的 qubits 消掉。

基本流程：

整体 quantum state
        ↓
构造整体 density matrix
        ↓
对不关心的 subsystem 做 partial trace
        ↓
得到目标 subsystem 的 density matrix

可以写成：

ρA = TrB(ρAB)

其中：

ρAB = 整个系统的 density matrix
B   = 不关心的 subsystem
A   = 我们关心的 subsystem
ρA  = A 的完整 quantum state

7. 和 Classical Subsystem 的区别

Classical system

probability
    ↓
对不关心的 bits 求和
    ↓
subsystem probability distribution

例如：

P(b1 = 0)
= p000 + p001 + p010 + p011

Quantum system

不能直接：

amplitude 求和

如果只求测量概率：

amplitude
    ↓
|α|²
    ↓
probability
    ↓
对不关心的 qubits 求和
    ↓
measurement probability distribution

如果要完整描述 subsystem：

整体 quantum state
    ↓
density matrix
    ↓
partial trace
    ↓
subsystem density matrix

8. 核心总结

n-qubit system
│
├── 整体状态由 amplitudes 表示
│
│   α000, α001, ...
│
├── amplitude 不是 probability
│
│   P(x) = |αx|²
│
├── 不能直接把 amplitudes 相加
│
├── 如果只求 subsystem 的测量概率
│   │
│   └── |α|² → 概率 → 对其他 qubits 求和
│
└── 如果要完整描述 subsystem 的 quantum state
    │
    └── density matrix + partial trace

最重要的三句话：

1. Quantum state 中存的是 probability amplitude，不是 probability。

2. 如果只求 subsystem 的测量概率分布，要先对 amplitude 取模平方，再对不关心的 qubits 求和。

3. 如果要完整表示 subsystem 的量子态，则需要 density matrix 和 partial trace，而不只是概率分布。
