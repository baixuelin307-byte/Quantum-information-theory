
# 6. Systems with Multiple Bits and Multiple Qubits

## 1. Multiple Classical Bits

一个 classical bit 只有两个可能值：

`0`

或者：

`1`

如果有两个 bits：

`00, 01, 10, 11`

一共有：

`2² = 4`

种可能状态。

如果有三个 bits：

`000, 001, 010, 011, 100, 101, 110, 111`

一共有：

`2³ = 8`

种可能状态。

一般来说：

`n bits → 2ⁿ 个 possible bit strings`

可以统一写成：

`x ∈ {0,1}ⁿ`

---

## 2. Classical Probability State

如果我们不知道 n-bit system 当前到底是哪一个 bit string，就可以用 probability distribution 来表示。

例如两个 bits：

`P(00), P(01), P(10), P(11)`

它们必须满足：

`P(00) + P(01) + P(10) + P(11) = 1`

并且：

`P(x) ≥ 0`

所以一个 n-bit probabilistic state，本质上可以写成一个有 `2ⁿ` 个分量的 probability vector。

例如两个 bits：

`p = (p₀₀, p₀₁, p₁₀, p₁₁)`

并且：

`p₀₀ + p₀₁ + p₁₀ + p₁₁ = 1`

---

## 3. Simplex

所有合法的 classical probability distributions 满足：

`pᵢ ≥ 0`

以及：

`Σᵢ pᵢ = 1`

这些 probability vectors 组成的几何区域叫做：

`simplex`

可以简单理解为：

> simplex = 所有合法 classical probability distributions 组成的集合。

---

# 4. Multiple Qubits

一个 qubit 的 computational basis 是：

`|0⟩, |1⟩`

两个 qubits 的 computational basis 是：

`|00⟩, |01⟩, |10⟩, |11⟩`

一共有：

`2² = 4`

个 basis states。

三个 qubits 的 computational basis 是：

`|000⟩, |001⟩, |010⟩, |011⟩, |100⟩, |101⟩, |110⟩, |111⟩`

一共有：

`2³ = 8`

个 basis states。

一般来说：

`n qubits → 2ⁿ 个 computational basis states`

因此：

`n qubits → 2ⁿ-dimensional Hilbert space`

---

## 5. n-qubit 的一般状态

一个 n-qubit quantum state 可以写成：

`|ψ⟩ = Σₓ αₓ|x⟩`

其中：

- `x ∈ {0,1}ⁿ`
- `|x⟩` 是 computational basis state
- `αₓ` 是对应的 probability amplitude

注意：

`αₓ` 不是 probability。

真正的 probability 是：

`|αₓ|²`

---

## 6. Two-Qubit State

例如两个 qubits：

`|ψ⟩ = α₀₀|00⟩ + α₀₁|01⟩ + α₁₀|10⟩ + α₁₁|11⟩`

这里有 4 个 probability amplitudes：

`α₀₀`

`α₀₁`

`α₁₀`

`α₁₁`

它们必须满足 normalization condition：

`|α₀₀|² + |α₀₁|² + |α₁₀|² + |α₁₁|² = 1`

---

## 7. Three-Qubit State

三个 qubits 的一般状态可以写成：

`|ψ⟩ = α₀₀₀|000⟩ + α₀₀₁|001⟩ + ... + α₁₁₁|111⟩`

一共有：

`2³ = 8`

个 amplitudes。

一般来说：

`n qubits → 2ⁿ 个 amplitudes`

并满足：

`Σₓ |αₓ|² = 1`

---

# 8. Measurement

如果：

`|ψ⟩ = Σₓ αₓ|x⟩`

然后对整个系统进行 computational basis measurement，

那么得到 bit string `x` 的 probability 是：

`P(x) = |αₓ|²`

measurement 之后，state collapse 到：

`|x⟩`

---

例如：

`|ψ⟩ = α₀₀|00⟩ + α₀₁|01⟩ + α₁₀|10⟩ + α₁₁|11⟩`

测量以后可能得到：

`00`

或者：

`01`

或者：

`10`

或者：

`11`

对应概率分别是：

`|α₀₀|²`

`|α₀₁|²`

`|α₁₀|²`

`|α₁₁|²`

并且：

`|α₀₀|² + |α₀₁|² + |α₁₀|² + |α₁₁|² = 1`

---

# 9. 多个 Qubit 能表达更多状态

一个 qubit 可以写成：

`|ψ⟩ = α|0⟩ + β|1⟩`

它可以处于很多不同的 quantum states。

例如：

`|0⟩`

`|1⟩`

`|+⟩`

`|−⟩`

以及一般形式：

`α|0⟩ + β|1⟩`

其中：

`|α|² + |β|² = 1`

---

多个 qubits 也一样，但是 state space 会快速变大：

```text
1 qubit → 2 个 basis states

2 qubits → 4 个 basis states

3 qubits → 8 个 basis states

n qubits → 2ⁿ 个 basis states
