# Proof of the Nonsingularity of $\mathbf{D}$ and $\mathbf{I}-\mathbf{R}^{C}$

## A. Definitions and Assumptions

Consider a carbon emission flow (CEF) network with $n$ buses. For each bus $i$, let $P_i^{\mathrm{in}}$ denote the total active power mixed at that bus. The diagonal power-mixing matrix is defined as

```math
\mathbf{D} = \mathrm{diag} \left( P_1^{\mathrm{in}}, P_2^{\mathrm{in}}, \ldots, P_n^{\mathrm{in}} \right).
```

<p align="right">(A1)</p>

Let $P_{ik}^{k}\ge 0$ denote the active power transmitted from bus $i$ to a downstream bus $k$, measured at the receiving end $k$. The CEF transfer matrix $\mathbf{R}^{C}\in\mathbb{R}^{n\times n}$ is defined by

```math
R_{ik}^{C} = \begin{cases} \dfrac{P_{ik}^{k}}{P_i^{\mathrm{in}}}, & k\in\mathcal{N}_i^{-},\\[6pt] 0, & \text{otherwise}, \end{cases}
```

<p align="right">(A2)</p>

where $\mathcal{N}_i^{-}$ is the set of downstream buses receiving carbon-carrying active power from bus $i$.

The proof is established under the following standard CEF transfer conditions.

**Assumption 1:** Every retained bus has positive mixed active power:

```math
P_i^{\mathrm{in}}>0, \qquad \forall i\in\mathcal{N}.
```

<p align="right">(A3)</p>

**Assumption 2:** The total downstream receiving-end power attributed to bus $i$ does not exceed the mixed active power at that bus:

```math
\sum_{k\in\mathcal{N}_i^{-}}P_{ik}^{k} \le P_i^{\mathrm{in}}, \qquad \forall i\in\mathcal{N}.
```

<p align="right">(A4)</p>

**Assumption 3:** From every bus, there exists a directed path in the CEF transfer graph to at least one bus $r$ satisfying

```math
\sum_{k=1}^{n}R_{rk}^{C}<1.
```

<p align="right">(A5)</p>

A bus satisfying (A5) is hereafter called a **deficient bus**. Assumption 3 excludes an isolated, lossless, closed transfer component in which carbon-carrying power circulates indefinitely without reaching any local consumption, loss, or other outflow not represented by $\mathbf{R}^{C}$.

---

## B. Main Theorem

**Theorem 1:** Under Assumptions 1-3, both $\mathbf{D}$ and $\mathbf{I}-\mathbf{R}^{C}$ are nonsingular. Consequently, the recursive CEF multiplier relation admits the unique compact-form solution

```math
-\boldsymbol{\lambda}_{\mathrm{CEF}} = \left(\mathbf{I}-\mathbf{R}^{C}\right)^{-1} \mathbf{D}^{-1} \boldsymbol{\mu}_{\mathrm{NCI}}.
```

<p align="right">(A6)</p>

### Proof

#### 1. Nonsingularity of $\mathbf{D}$

By Assumption 1, every diagonal entry of $\mathbf{D}$ is strictly positive. Therefore,

```math
\det(\mathbf{D}) = \prod_{i=1}^{n}P_i^{\mathrm{in}} >0.
```

<p align="right">(A7)</p>

Hence, $\mathbf{D}$ is nonsingular, and its inverse is

```math
\mathbf{D}^{-1} = \mathrm{diag} \left( \frac{1}{P_1^{\mathrm{in}}}, \frac{1}{P_2^{\mathrm{in}}}, \ldots, \frac{1}{P_n^{\mathrm{in}}} \right).
```

<p align="right">(A8)</p>

#### 2. Substochasticity of $\mathbf{R}^{C}$

From (A2), all entries of $\mathbf{R}^{C}$ are nonnegative:

```math
\mathbf{R}^{C}\ge \mathbf{0}.
```

<p align="right">(A9)</p>

Using Assumption 2, the sum of row $i$ satisfies

```math
\sum_{k=1}^{n}R_{ik}^{C} = \frac{\displaystyle\sum_{k\in\mathcal{N}_i^{-}}P_{ik}^{k}} {P_i^{\mathrm{in}}} \le 1.
```

<p align="right">(A10)</p>

Thus, $\mathbf{R}^{C}$ is a nonnegative substochastic matrix. Its induced infinity norm satisfies

```math
\left\|\mathbf{R}^{C}\right\|_{\infty} = \max_i\sum_{k=1}^{n}R_{ik}^{C} \le 1.
```

<p align="right">(A11)</p>

Therefore, its spectral radius obeys

```math
\rho\!\left(\mathbf{R}^{C}\right) \le \left\|\mathbf{R}^{C}\right\|_{\infty} \le 1.
```

<p align="right">(A12)</p>

It remains to exclude the case $\rho(\mathbf{R}^{C})=1$.

#### 3. Strict Bound on the Spectral Radius

Assume, for contradiction, that

```math
\rho\!\left(\mathbf{R}^{C}\right)=1.
```

<p align="right">(A13)</p>

Because $\mathbf{R}^{C}$ is nonnegative, the Perron-Frobenius theorem guarantees the existence of a nonzero vector $\mathbf{v}\ge\mathbf{0}$ such that

```math
\mathbf{R}^{C}\mathbf{v}=\mathbf{v}.
```

<p align="right">(A14)</p>

Let

```math
M=\max_{1\le i\le n}v_i>0, \qquad \mathcal{S}=\{i\mid v_i=M\}.
```

<p align="right">(A15)</p>

For any $i\in\mathcal{S}$, (A14) gives

```math
M =v_i =\sum_{k=1}^{n}R_{ik}^{C}v_k \le M\sum_{k=1}^{n}R_{ik}^{C} \le M.
```

<p align="right">(A16)</p>

Since the first and last terms in (A16) are equal, both inequalities must hold with equality. Equality in the second inequality of (A16) requires

```math
\sum_{k=1}^{n}R_{ik}^{C}=1, \qquad \forall i\in\mathcal{S}.
```

<p align="right">(A17)</p>

Moreover, equality in the first inequality of (A16) requires

```math
v_k=M \quad \text{for every }k\text{ such that }R_{ik}^{C}>0.
```

<p align="right">(A18)</p>

Therefore, every positive-transfer successor of a bus in $\mathcal{S}$ also belongs to $\mathcal{S}$. Hence, $\mathcal{S}$ is closed under all directed CEF transfer paths. In addition, (A17) shows that no bus in $\mathcal{S}$ is deficient.

However, Assumption 3 states that every bus, including every bus in $\mathcal{S}$, has a directed path to a deficient bus. Since $\mathcal{S}$ is closed under directed transfer paths, that deficient bus must also belong to $\mathcal{S}$, which contradicts (A17). Therefore, the assumption in (A13) is false, and

```math
\rho\!\left(\mathbf{R}^{C}\right)<1.
```

<p align="right">(A19)</p>

#### 4. Nonsingularity of $\mathbf{I}-\mathbf{R}^{C}$

Suppose that $\mathbf{I}-\mathbf{R}^{C}$ were singular. Then there would exist a nonzero vector $\mathbf{y}$ satisfying

```math
\left(\mathbf{I}-\mathbf{R}^{C}\right)\mathbf{y} =\mathbf{0},
```

<p align="right">(A20)</p>

which implies

```math
\mathbf{R}^{C}\mathbf{y}=\mathbf{y}.
```

<p align="right">(A21)</p>

Thus, $1$ would be an eigenvalue of $\mathbf{R}^{C}$, yielding

```math
\rho\!\left(\mathbf{R}^{C}\right)\ge 1,
```

<p align="right">(A22)</p>

in contradiction with (A19). Hence,

```math
\det\!\left(\mathbf{I}-\mathbf{R}^{C}\right)\ne 0,
```

<p align="right">(A23)</p>

and $\mathbf{I}-\mathbf{R}^{C}$ is nonsingular.

Since both $\mathbf{D}$ and $\mathbf{I}-\mathbf{R}^{C}$ are nonsingular, the recursive multiplier relation has the unique solution given by (A6).

---

## C. Corollary and Interpretation

**Corollary 1:** Under Assumptions 1-3, the inverse of $\mathbf{I}-\mathbf{R}^{C}$ admits the convergent Neumann-series representation

```math
\left(\mathbf{I}-\mathbf{R}^{C}\right)^{-1} = \sum_{\ell=0}^{\infty} \left(\mathbf{R}^{C}\right)^{\ell}.
```

<p align="right">(A24)</p>

### Proof

Equation (A19) gives $\rho(\mathbf{R}^{C})<1$, which is the necessary and sufficient condition for convergence of the matrix geometric series in (A24).

Substituting (A24) into (A6) gives

```math
-\boldsymbol{\lambda}_{\mathrm{CEF}} = \sum_{\ell=0}^{\infty} \left(\mathbf{R}^{C}\right)^{\ell} \mathbf{D}^{-1} \boldsymbol{\mu}_{\mathrm{NCI}}.
```

<p align="right">(A25)</p>

Equation (A25) shows that the CEF multiplier consists of the effects of binding NCI caps transferred over CEF paths of different lengths. The term with $\ell=0$ represents the local contribution, whereas the terms with $\ell\ge1$ represent contributions transferred through increasingly long power-flow paths.

---

## D. Scope of the Result

The nonsingularity of $\mathbf{I}-\mathbf{R}^{C}$ does not follow solely from the nonnegativity of $\mathbf{R}^{C}$. Assumption 3 is essential. If the CEF transfer graph contains a closed component in which every row sum equals one, then that component may sustain a unit eigenvalue, making $\mathbf{I}-\mathbf{R}^{C}$ singular.

In a physically meaningful CEF network, Assumption 3 is satisfied when every carbon-carrying transfer path eventually reaches a bus with local demand, active-power loss, or another mechanism that makes the corresponding row sum strictly less than one.
