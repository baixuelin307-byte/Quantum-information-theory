Local Unitary Operation 在多 Qubit 系统中的表示

1. 基本概念

在一个多 qubit 系统中，我们可以只对其中某一个 qubit 或某一个 subsystem 施加 unitary operation。

例如，在一个 2-qubit system 中：

q1 → 不做操作
q2 → 做 U

那么整体操作写成：

I ⊗ U

其中：

I = identity operation
U = 作用在第二个 qubit 上的 unitary operation

因此：

I ⊗ U

表示：

第一个 qubit：不改变
第二个 qubit：按照 U 演化

2. 为什么不能只写 U？

单个 qubit 的状态是 2 维的，因此单 qubit unitary matrix 是：

2 × 2

例如：

U = [u00  u01
     u10  u11]

但是一个 2-qubit system 的 state vector 是 4 维：

|00⟩
|01⟩
|10⟩
|11⟩

所以作用在整个 2-qubit system 上的 operation 必须是：

4 × 4

因此需要使用 tensor product，把局部的 U 扩展到整个系统：

I ⊗ U

3. I ⊗ U 的矩阵形式

假设：

U = [u00  u01
     u10  u11]

那么：

I ⊗ U =

[u00  u01   0    0
 u10  u11   0    0
  0    0   u00  u01
  0    0   u10  u11]

也可以理解为：

[ U   0
  0   U ]

4. 第一个 Qubit 会不会被 U 改变？

不会。

因为第一个 qubit 上作用的是：

I

而 identity operation 满足：

I|ψ⟩ = |ψ⟩

所以第一个 qubit 保持原来的状态。

例如：

|00⟩ = |0⟩ ⊗ |0⟩

经过：

I ⊗ U

得到：

(I ⊗ U)|00⟩
= |0⟩ ⊗ U|0⟩

第一位仍然是：

|0⟩

只有第二位发生变化。

同样：

(I ⊗ U)|10⟩
= |1⟩ ⊗ U|0⟩

第一位原来是 |1⟩，之后仍然是 |1⟩。

5. 第一个 Qubit 不是“没有参与”

需要注意：

第一个 qubit 不是被忽略了，而是它在整体 operation 中受到的是 identity operation。

因此：

I ⊗ U

表示：

第一个 qubit：参与整体系统，但不发生改变
第二个 qubit：受到 U 的作用

6. 对 Computational Basis 的作用

对于 2-qubit computational basis：

|00⟩
|01⟩
|10⟩
|11⟩

I ⊗ U 的作用分别为：

|00⟩ → |0⟩ ⊗ U|0⟩
|01⟩ → |0⟩ ⊗ U|1⟩
|10⟩ → |1⟩ ⊗ U|0⟩
|11⟩ → |1⟩ ⊗ U|1⟩

可以看到：

第一位保持不变
第二位按照 U 演化

7. 如果操作的是第一个 Qubit

如果只对第一个 qubit 做 U，而第二个 qubit 不变，那么整体 operation 是：

U ⊗ I

因此：

I ⊗ U
→ 对第二个 qubit 做 U

U ⊗ I
→ 对第一个 qubit 做 U

8. 推广到 n-Qubit System

对于 n-qubit system，如果只对某一个 qubit 做 U，其他 qubits 不改变，就在其他位置放 identity：

I ⊗ I ⊗ ... ⊗ U ⊗ ... ⊗ I

例如，有 5 个 qubits，只对第 3 个 qubit 做 U：

I ⊗ I ⊗ U ⊗ I ⊗ I

9. U、V、S 这些符号是什么？

U、V、S 等符号通常只是表示某个 unitary operation。

它们本身不一定对应固定的 gate。

例如：

U
V
S

可以分别代表不同的 local unitary operations。

只有像下面这些符号通常有固定含义：

X
Y
Z
H
CNOT

所以：

U、V、S 更多是对某个局部 unitary operation 的一般记号。

10. Unitary Evolution

对于封闭量子系统中的 quantum gate，状态改变遵循：

|ψ'⟩ = U|ψ⟩

其中：

U†U = I

这保证量子态保持 normalization：

||ψ'||² = 1

即使只对局部 subsystem 做操作，从整个系统来看，仍然对应整体 Hilbert space 上的 unitary evolution。

11. 不做 Local Operation 时

在理想 quantum circuit 模型中：

不做操作

通常等价于：

I

即：

I|ψ⟩ = |ψ⟩

所以这一段状态保持不变。

但在真实量子通信系统中，不施加 local control 并不一定代表量子态完全不演化，它仍可能受到：

自身 Hamiltonian
quantum channel
noise
decoherence
photon loss

等因素影响。

因此要区分：

Quantum circuit abstraction:
没有 gate → I → 状态不变

Real physical system:
没有主动控制 → 仍可能发生自然演化或信道演化

12. 核心总结

Local Unitary Operation
│
├── 只作用在某个 qubit / subsystem
│
├── 其他 qubits 用 I 表示
│
├── 通过 tensor product 扩展到整个系统
│
├── 没被操作的 qubit 不是被忽略
│   └── 而是受到 identity operation
│
└── 整体仍然满足 unitary evolution

最重要的例子：

I ⊗ U

表示：

q1 → I → 不改变
q2 → U → 发生演化

而：

U ⊗ I

表示：

q1 → U → 发生演化
q2 → I → 不改变

一句话记住：

Local unitary operation 只改变目标 subsystem，但在整个多 qubit 系统中，需要用 identity 和 tensor product 把局部操作扩展成完整的 unitary operation。
