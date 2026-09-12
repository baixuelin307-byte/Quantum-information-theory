5.1 Communicating a Trit Using a Qubit

1. 任务目标

Alice 手里有一个 trit：

a ∈ {0, 1, 2}

她希望把这个信息发送给 Bob。

如果只允许发送一个 classical bit，那么 Alice 只能发送：

0

或者：

1

但是 trit 有三个可能值，因此一个 bit 不可能把三个值全部完美区分。

2. Classical Bit Strategy

一个简单的 classical bit strategy 可以是：

trit 0 → 发送 bit 0

trit 1 → 发送 bit 1

trit 2 → 也发送 bit 1

Bob 收到：

bit 0 → 猜 trit 0

bit 1 → 猜 trit 1

三个输入的成功率分别是：

1, 1, 0

所以：

P_worst = 0

也就是说，某一个输入会被完全牺牲。

3. Randomized Bit Strategy

为了避免某一个 trit 永远失败，可以加入随机策略。

通过适当随机化，可以让三个输入的 worst-case success probability 都达到：

1/2

因此 classical bit strategy 的最优 worst-case performance 是：

P_worst(bit) = 1/2 = 50%

这是后面和 qubit strategy 比较的基准。

4. Qubit Strategy

Alice 可以把三个 trit 编码成三个不同的 qubit states：

0 → |φ₀⟩

1 → |φ₁⟩

2 → |φ₂⟩

这三个状态构成对称的 trine states。

它们在二维空间中大致呈现 120° 对称结构：

            |φ₁⟩
           /
          /
         O------> |φ₀⟩
          \
           \
            |φ₂⟩

由于 qubit 是二维系统，不可能存在三个两两正交的状态，因此：

一个 qubit 不能完美编码并区分一个 trit。

但是，可以通过合适的 measurement，让判断成功率高于 classical bit。

5. Trine States 的重要性质

三个对称状态满足：

|ψ₀⟩⟨ψ₀| + |ψ₁⟩⟨ψ₁| + |ψ₂⟩⟨ψ₂| = (3/2)I

这里的 (3/2)I 不是人为规定的，而是把三个具体的 trine state projection matrices 相加得到的。

例如可以取：

|ψ₀⟩ = (1, 0)

|ψ₁⟩ = (-1/2, √3/2)

|ψ₂⟩ = (-1/2, -√3/2)

对应的 projection matrices 是：

|ψ₀⟩⟨ψ₀| =
[ 1   0 ]
[ 0   0 ]

|ψ₁⟩⟨ψ₁| =
[ 1/4      -√3/4 ]
[ -√3/4     3/4  ]

|ψ₂⟩⟨ψ₂| =
[ 1/4       √3/4 ]
[  √3/4      3/4 ]

三个矩阵相加时，非对角项互相抵消：

-√3/4 + √3/4 = 0

最后得到：

[ 3/2   0   ]
[  0   3/2  ]

也就是：

(3/2)I

因此：

|ψ₀⟩⟨ψ₀| + |ψ₁⟩⟨ψ₁| + |ψ₂⟩⟨ψ₂| = (3/2)I

6. 为什么会出现 2/3？

一个合法的 POVM measurement 需要满足：

E₀ + E₁ + E₂ = I

但是刚才三个 projection 相加得到：

(3/2)I

所以需要乘一个 normalization factor：

2/3

因为：

(2/3) × (3/2) = 1

因此定义：

Eᵢ = (2/3)|ψᵢ⟩⟨ψᵢ|

于是：

Σᵢ Eᵢ = (2/3) Σᵢ |ψᵢ⟩⟨ψᵢ|

代入：

Σᵢ Eᵢ = (2/3) × (3/2)I = I

所以这里的 2/3 本质上就是一个 normalization factor。

7. 为什么成功率可以达到 2/3？

如果 Alice 发送：

|ψᵢ⟩

Bob 正确得到 measurement outcome i 的概率是：

P(i|i) = ⟨ψᵢ|Eᵢ|ψᵢ⟩

代入：

Eᵢ = (2/3)|ψᵢ⟩⟨ψᵢ|

得到：

P(i|i) = (2/3)⟨ψᵢ|ψᵢ⟩⟨ψᵢ|ψᵢ⟩

由于：

⟨ψᵢ|ψᵢ⟩ = 1

所以：

P(i|i) = 2/3

因此：

P(success|0) = 2/3

P(success|1) = 2/3

P(success|2) = 2/3

于是：

P_worst(qubit) = 2/3 ≈ 66.7%

8. Classical Bit 和 Qubit 的比较

Classical bit：

P_worst(bit) = 1/2 = 50%

Qubit：

P_worst(qubit) = 2/3 ≈ 66.7%

所以：

2/3 > 1/2

这说明：

一个 qubit 虽然不能完美存储一个 trit，但在这个 communication task 中，可以比一个 classical bit 保留更多关于 trit 的信息。

9. 图中的紫色和红色方向

图中：

紫色：Alice 编码 trit 使用的三个 states
|φ₀⟩, |φ₁⟩, |φ₂⟩

红色：Bob 的三个 measurement directions
|φ₀⊥⟩, |φ₁⊥⟩, |φ₂⊥⟩

可以理解为：

紫色 = candidate quantum states
红色 = measurement directions

它们不是同一个概念。

Bob 的任务是通过 measurement outcome 来推断 Alice 原来发送的是哪一个紫色状态。

10. 书中给出的一个简单测量策略

书里先介绍了一个比较直观、但不是最优的 measurement strategy。

Bob 随机选择：

k ∈ {0, 1, 2}

然后使用正交基：

{|φₖ⟩, |φₖ⊥⟩}

进行测量。

也就是说，Bob 随机挑一个候选态 |φₖ⟩，然后测试：

收到的 qubit 更接近 |φₖ⟩，还是它的正交方向 |φₖ⊥⟩？

11. Bob 根据测量结果怎么猜？

如果 measurement outcome 是：

|φₖ⟩

Bob 就猜：

ℓ = k

也就是说：

Bob 认为 Alice 发送的就是第 k 个 trit。

如果 measurement outcome 是：

|φₖ⊥⟩

Bob 就认为原来的状态不是 |φₖ⟩，于是从剩下两个 trit 中随机选择一个作为答案。

12. 这个简单测量策略的成功率

情况 1：Bob 随机选中的 k 刚好等于真实 trit

这种情况发生概率：

1/3

如果：

k = ℓ

那么 Bob 正好用：

{|φₗ⟩, |φₗ⊥⟩}

去测量真实状态：

|φₗ⟩

因此：

P(success | k = ℓ) = 1

这一部分对总成功率的贡献是：

(1/3) × 1

情况 2：Bob 选中的 k 不等于真实 trit

这种情况发生概率：

2/3

即：

k ≠ ℓ

此时 Bob 用：

{|φₖ⟩, |φₖ⊥⟩}

去测量真实状态：

|φₗ⟩

由于 trine states 之间存在固定角度关系，测量得到：

|φₖ⊥⟩

的概率是：

3/4

如果得到 |φₖ⊥⟩，Bob 在剩下两个 trit 中随机猜一个，因此猜对概率是：

1/2

所以这一部分的成功概率贡献是：

(2/3) × (3/4) × (1/2)

13. 总成功率

因此：

P_success = (1/3)×1 + (2/3)×(3/4)×(1/2)

计算：

P_success = 1/3 + 1/4 = 7/12

所以：

P_success = 7/12 ≈ 58.3%

14. 为什么 7/12 已经说明 qubit 比 bit 强？

因为前面已经知道：

P_worst(bit) = 1/2 = 50%

而这个简单的 qubit strategy：

P_success = 7/12 ≈ 58.3%

所以：

7/12 > 1/2

也就是：

58.3% > 50%

因此已经可以证明：

存在一种 qubit strategy，可以超过所有 classical bit strategies。

15. 但是 7/12 还不是最优

书里紧接着说明：

7/12

还不是 qubit strategy 的最好结果。

还可以设计更好的 measurement，使成功率继续提高。

因此这里的 7/12 主要作用是：

先证明 qubit 确实可以 outperform classical bit。

16. 整个通信流程

Alice 得到 trit 0/1/2
→ 编码成三个不同 qubit states 之一
→ 把 qubit 发送给 Bob
→ Bob 选择 measurement
→ 得到 measurement outcome
→ 根据 outcome 猜原来的 trit

17. 核心区别

Classical bit 只有两个可以完美区分的编码：

0

和：

1

但是 Alice 有三个输入：

0, 1, 2

所以一定需要丢失一部分信息。

Qubit 虽然也是二维系统，不能提供三个两两正交的状态，但是它可以利用：

non-orthogonal states

probability amplitudes

phase

quantum measurement

把三个 trit 更均匀地编码进一个 qubit。

因此在某些任务指标上：

P_qubit > P_bit

18. 一句话总结

一个 qubit 不能完美传递一个 trit，因为二维 Hilbert space 中不存在三个两两正交的量子态；但是 Alice 可以把三个 trit 编码成三个对称的 non-orthogonal qubit states，Bob 再设计合适的 measurement，从而使 worst-case success probability 超过 classical bit。

最重要的比较：

P_worst(bit) = 1/2 = 50%

简单 qubit strategy：

P_success = 7/12 ≈ 58.3%

更好的对称 POVM：

P_success = 2/3 ≈ 66.7%

其中：

|ψ₀⟩⟨ψ₀| + |ψ₁⟩⟨ψ₁| + |ψ₂⟩⟨ψ₂| = (3/2)I

这个 (3/2)I 是三个 trine state projection matrices 实际相加得到的，不是人为定义的。

为了构造合法 POVM：

E₀ + E₁ + E₂ = I

定义：

Eᵢ = (2/3)|ψᵢ⟩⟨ψᵢ|

因为：

(2/3) × (3/2) = 1

所以：

Σᵢ Eᵢ = I

最终：

P(i|i) = 2/3 = 66.7%
