# What is a Qubit?

## 1. Classical Bit

可以从两个角度理解 bit。

### 1.1 操作性的角度

可以把 bit 看成：

> 一个能够存储 0 或 1，并且可以把其中的信息读取出来的系统。

一个 classical bit 的状态只有两种：

$0$

或：

$1$

同时，我们还可以对 bit 进行操作。

例如 NOT gate：

$0 \rightarrow 1$

$1 \rightarrow 0$

也就是说，bit 不仅可以存储信息，也可以被读取和修改。

---

### 1.2 信息的角度

从信息的角度看，可以把复杂的信息编码成很多个 0 和 1 的组合。

例如：

`01001101...`

这些 0 和 1 的组合共同构成一个信息系统。

因此，可以把 classical bit 理解为：

> **使用 0 和 1 来存储、读取和修改信息的基本单位。**

---

# 2. A Simple Analog Model of Information

Analog model 和 classical digital bit 不一样。

Digital bit 只能取：

$0$

或：

$1$

但是 analog model 可以在一个连续区间内取值，例如：

$0.1265$

$0.7895$

$0.5321$

等等。

也就是说，它不再只有两个离散状态，而是可以连续变化。

---

## 2.1 Analog Set Device

Analog set device 可以把系统设置为 0 到 1 之间的任意值。

例如：

$0.2$

$0.73$

$0.999$

---

## 2.2 Analog Read Device

Analog read device 用来读取当前系统所存储的连续值。

例如：

`读取结果 = 0.7895`

---

## 2.3 Analog Transformation

还可以通过某个函数对 analog information 进行变换。

例如：

$x \rightarrow f(x)$

输入：

$x \in [0,1]$

经过 transformation 后得到：

$f(x) \in [0,1]$

因此 analog information 也可以被：

- 设置
- 读取
- 修改

但它的状态空间是连续的。

---

# 3. A Simple Probabilistic Digital Model of Information

这个模型仍然是一个 digital model。

也就是说，bit 的真实状态仍然只有：

$0$

或：

$1$

但是我们不一定知道它当前是哪一个状态。

因此，可以使用概率描述：

$P(0)=0.3$

$P(1)=0.7$

意思是：

- 有 30% 的概率是 0
- 有 70% 的概率是 1

可以写成一个概率向量：

$(0.3,\ 0.7)$

并且满足：

$P(0)+P(1)=1$

---

## 3.1 关键理解

这里非常重要：

> **概率模型并没有改变 bit 本身。**

真实 bit 仍然只是：

$0$

或者：

$1$

概率只是描述：

> **我们对这个 bit 当前状态的不确定性。**

所以：

`Probabilistic bit = classical bit + probability description`

---

# 4. A Simple Quantum Model of Information

量子信息模型和前面的 classical model 有本质区别。

但是，把 qubit 和 analog model、probabilistic model 放在一起比较，可以帮助理解 qubit 的结构。

---

## 4.1 Qubit 的基本表示

一个 qubit 的一般状态可以写成：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

其中：

- $\alpha_0$：对应 $|0\rangle$ 的 probability amplitude
- $\alpha_1$：对应 $|1\rangle$ 的 probability amplitude

$\alpha_0$ 和 $\alpha_1$ 叫做：

**probability amplitudes（概率幅）**

注意：

> **概率幅本身不是概率。**

真正的测量概率是：

$P(0)=|\alpha_0|^2$

$P(1)=|\alpha_1|^2$

---

# 5. Probability Amplitude

概率幅和普通概率不同。

普通概率只有大小，例如：

$0.3$

$0.7$

而概率幅一般是复数。

因此，概率幅除了有大小，还包含：

**phase（相位）**

这就是 classical probability 和 quantum probability amplitude 的一个重要区别。

---

## 5.1 概率幅向量

一个 qubit 可以写成 probability amplitude vector：

$(\alpha_0,\ \alpha_1)$

也可以理解为：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

其中：

$\alpha_0,\alpha_1\in\mathbb{C}$

也就是说：

> 概率幅属于复数域。

---

## 5.2 Normalization

qubit 的 probability amplitude vector 必须满足归一化条件：

$|\alpha_0|^2+|\alpha_1|^2=1$

这表示：

$P(0)+P(1)=1$

其中：

$|\alpha_0|^2$

表示测量得到 0 的概率。

而：

$|\alpha_1|^2$

表示测量得到 1 的概率。

所以：

$P(0)=|\alpha_0|^2$

$P(1)=|\alpha_1|^2$

---

# 6. Phase

概率幅不仅决定测量概率，还包含 phase。

例如一个复数可以写成：

$re^{i\phi}$

其中：

- $r$：大小
- $\phi$：phase
- $i$：虚数单位

并且：

$i^2=-1$

因此一个 probability amplitude 可以同时包含：

- magnitude
- phase

---

# 7. Qubit 的角度表示

单个 qubit 可以写成：

$|\psi\rangle=\sin(\theta)|0\rangle+e^{i\phi}\cos(\theta)|1\rangle$

其中：

$\alpha_0=\sin(\theta)$

$\alpha_1=e^{i\phi}\cos(\theta)$

这种写法自动满足：

$|\alpha_0|^2+|\alpha_1|^2=1$

因为：

$\sin^2(\theta)+\cos^2(\theta)=1$

---

## 7.1 $\theta$ 的作用

$\theta$ 主要决定：

$|0\rangle$

和：

$|1\rangle$

两个分量的大小比例。

例如：

- $\sin(\theta)$ 越大，$|0\rangle$ 分量越大
- $\cos(\theta)$ 越大，$|1\rangle$ 分量越大

因此 $\theta$ 主要影响：

$P(0)$

和：

$P(1)$

---

## 7.2 $\phi$ 的作用

$\phi$ 决定两个分量之间的：

**relative phase（相对相位）**

也就是说：

$\phi$

不是简单控制“有多少概率是 0 或 1”，而是控制：

> $|0\rangle$ 和 $|1\rangle$ 两个 probability amplitudes 之间的相位关系。

这个 phase 会影响：

- interference
- state distinguishing
- quantum computation
- measurement results in different bases

---

# 8. Qubit 在测量之前是什么？

在测量之前，qubit 的状态可以是：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

也就是说，它可以处于：

$|0\rangle$

和：

$|1\rangle$

的 superposition（叠加态）。

这并不是说 qubit 在测量前已经偷偷确定为 0 或 1。

而是说：

> qubit 本身处在一个由 probability amplitude 和 phase 描述的量子状态中。

---

# 9. 测量 Qubit

如果使用 computational basis：

$\{|0\rangle,|1\rangle\}$

进行测量，那么测量结果只能是：

$0$

或者：

$1$

并且：

$P(0)=|\alpha_0|^2$

$P(1)=|\alpha_1|^2$

测量之后，量子态会坍缩到对应的测量状态。

例如：

如果测量结果是 0：

$|\psi\rangle\rightarrow|0\rangle$

如果测量结果是 1：

$|\psi\rangle\rightarrow|1\rangle$

---

# 10. Classical Probability 和 Quantum Probability Amplitude 的区别

### Classical probabilistic model

使用：

$P(0),P(1)$

描述我们对真实 bit 的不确定性。

真实状态仍然已经是：

$0$

或：

$1$

---

### Quantum model

使用：

$\alpha_0,\alpha_1$

描述 qubit。

其中：

$P(0)=|\alpha_0|^2$

$P(1)=|\alpha_1|^2$

但是 probability amplitude 还包含：

**phase**

因此 quantum state 不只是普通概率分布。

---

# 11. 最核心的区别

可以简单理解为：

### Classical bit

`0 or 1`

---

### Probabilistic classical bit

`0 or 1 + probability`

例如：

$P(0)=0.3$

$P(1)=0.7$

---

### Qubit

`probability amplitude + phase`

也就是：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

其中：

$|\alpha_0|^2+|\alpha_1|^2=1$

---

# 12. 一句话理解 Qubit

> **Qubit 是由复数 probability amplitudes 描述的量子信息基本单位，它可以处在 $|0\rangle$ 和 $|1\rangle$ 的 superposition 中，而测量概率由 probability amplitude 的模平方决定。**

最基本的表达式：

$|\psi\rangle=\alpha_0|0\rangle+\alpha_1|1\rangle$

其中：

- $\alpha_0,\alpha_1$：probability amplitudes
- $|\alpha_0|^2$：测量得到 0 的概率
- $|\alpha_1|^2$：测量得到 1 的概率
- phase：包含在复数 probability amplitude 中
- $|\alpha_0|^2+|\alpha_1|^2=1$

---

## 最简单记忆

`bit = 0 or 1`

`probabilistic bit = 0 or 1 + probability`

`qubit = probability amplitude + phase + superposition`

最终测量：

`qubit → measurement → 0 or 1`
         







