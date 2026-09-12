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

例如一个 3-qubit state：

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

4. 如果只想求 Subsystem 的测量概率分布

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

所以：

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

写成：

ρA = TrB(ρAB)

其中：

ρAB = 整个系统的 density matrix
B   = 不关心的 subsystem
A   = 我们关心的 subsystem
ρA  = A 的完整 quantum state

所以：

density matrix + partial trace 主要用于完整表达 subsystem 的量子态，而不是单纯求概率分布。

7. Subsystem 上的 Quantum Operation

量子操作也可以只作用在某个 subsystem 上。

例如 3-qubit system 中，一个 unitary operation U 只作用在第一个 qubit：

q1 → U
q2 → 不变
q3 → 不变

从整个 3-qubit system 来看，这个操作写成：

U ⊗ I ⊗ I

其中：

U = 作用在第一个 qubit 上的 unitary operation
I = identity operation

也就是说：

即使一个 gate 只作用在部分 qubits 上，从整体系统来看，它仍然必须被理解为整个 Hilbert space 上的 operation。

8. Quantum Gate 仍然要满足 Unitary Evolution

对于封闭量子系统中的 quantum gate，状态改变必须满足：

unitary evolution

例如：

|ψ'> = (U ⊗ I ⊗ I)|ψ>

其中 U 必须满足：

U†U = I

这样可以保证：

||ψ'||² = 1

也就是总概率仍然保持为 1。

因此：

量子态改变
   ↓
不能随便改变
   ↓
通过 unitary operation 演化
   ↓
保持 normalization

即使 operation 只作用在 subsystem 上，整体依旧要满足 unitary evolution。

9. 多个 Local Operations

不同的 operations 可以作用在不同的 qubits 上。

例如：

U → 第一个 qubit
V → 第二、第三个 qubit
W → 第一、第二个 qubit

示意：

time →

q1 ── U ───────── W ──
q2 ─────── V ──── W ──
q3 ─────── V ─────────

这些都属于 local operations（局部操作）。

虽然它们只作用在部分 qubits 上，但从整个系统角度看，每一步都对应整个系统上的 unitary evolution。

10. Quantum Circuit

把不同的 unitary operations 按时间顺序作用在不同 qubits 上，就形成了：

quantum circuit

在 quantum circuit 中：

横线 = qubit
方框 = quantum gate / unitary operation
从左到右 = 时间演化

例如：

time →

q1 ── U ─────────
q2 ─────── V ────
q3 ─────── V ────

11. 两种理解 Quantum Circuit 的方式

方式一：qubit 沿 wire 流动

可以把它想象成：

qubit ── U ── V ── W ──>

qubit 从左往右经过不同 quantum gates，状态不断发生变化。

方式二：横轴表示时间

更准确的理解是：

horizontal axis = time

qubit 并不是物理上沿着线移动，而是：

随着时间向右推进，在不同时间点对 qubits 施加不同的 quantum operations。

12. 和 Classical Subsystem 的区别

Classical system

probability
    ↓
对不关心的 bits 求和
    ↓
subsystem probability distribution

例如：

P(b1 = 0)
= p000 + p001 + p010 + p011

Quantum system：只求测量概率

amplitude
    ↓
|α|²
    ↓
probability
    ↓
对不关心的 qubits 求和
    ↓
measurement probability distribution

Quantum system：完整描述 Subsystem

整体 quantum state
    ↓
density matrix
    ↓
partial trace
    ↓
subsystem density matrix

Quantum system：对 Subsystem 施加操作

local quantum gate
    ↓
扩展到整个系统
    ↓
例如 U ⊗ I ⊗ I
    ↓
整体仍满足 unitary evolution

13. 核心总结

n-qubit system
│
├── 整体状态
│   └── 用 probability amplitudes 表示
│
├── probability amplitude
│   └── P(x) = |αx|²
│
├── subsystem 的测量概率
│   └── |α|² 后，对其他 qubits 求和
│
├── subsystem 的完整 quantum state
│   └── density matrix + partial trace
│
├── local operation
│   └── 只作用在部分 qubits
│
├── 整体 operation
│   └── 例如 U ⊗ I ⊗ I
│
└── quantum circuit
    └── 多个 unitary operations 随时间作用在 qubits 上

最重要的几点：

1. Quantum state 中存的是 probability amplitude，而不是 probability。

2. amplitude 不能像 classical probability 一样直接相加。

3. 如果只求 subsystem 的测量概率分布：先取模平方，再对不关心的 qubits 求和。

4. 如果要完整表示 subsystem 的 quantum state：使用 density matrix 和 partial trace。

5. 对 subsystem 的 quantum gate 仍然属于整体系统的 unitary evolution，例如 U ⊗ I ⊗ I。

6. Quantum circuit 就是把这些 unitary operations 按时间顺序作用在不同 qubits 上。
