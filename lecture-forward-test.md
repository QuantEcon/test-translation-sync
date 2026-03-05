---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Solow Growth Model

This lecture introduces the [Solow growth model](https://en.wikipedia.org/wiki/Solow%E2%80%93Swan_model), one of the foundational models in macroeconomics for understanding long-run economic growth.

We will explore how capital accumulation, labor growth, and technological progress determine the steady-state level of output per capita.

## Setup

```{code-cell} ipython3
import numpy as np
import matplotlib.pyplot as plt
```

## The Model

Consider an economy with a production function

$$
Y_t = A K_t^{\alpha} L_t^{1-\alpha}
$$

where:

* $Y_t$ is total output at time $t$
* $K_t$ is the capital stock
* $L_t$ is the labor force
* $A$ is the technology parameter
* $\alpha \in (0,1)$ is the capital share

The capital accumulation equation is

$$
K_{t+1} = s Y_t + (1 - \delta) K_t
$$ (eq:capital-accum)

where $s \in (0,1)$ is the savings rate and $\delta \in (0,1)$ is the depreciation rate.

## Steady State

Defining $k_t = K_t / L_t$ as capital per worker, we can show that the steady-state capital per worker is

$$
k^* = \left(\frac{s A}{\delta + n}\right)^{\frac{1}{1-\alpha}}
$$ (eq:steady-state)

where $n$ is the population growth rate.

The [golden rule](https://en.wikipedia.org/wiki/Golden_Rule_savings_rate) savings rate that maximizes steady-state consumption is $s^* = \alpha$.

## Numerical Example

Let's compute and plot the transition dynamics.

```{code-cell} ipython3
# Parameters
A = 1.0      # technology
α = 0.33     # capital share
s = 0.25     # savings rate
δ = 0.05     # depreciation rate
n = 0.02     # population growth rate
T = 100      # time periods

# Steady state
k_star = (s * A / (δ + n)) ** (1 / (1 - α))
y_star = A * k_star ** α
print(f"Steady-state k* = {k_star:.4f}")
print(f"Steady-state y* = {y_star:.4f}")
```

```{code-cell} ipython3
# Transition dynamics
k = np.zeros(T)
k[0] = 1.0  # initial capital per worker

for t in range(T - 1):
    k[t+1] = (s * A * k[t]**α + (1 - δ) * k[t]) / (1 + n)
```

```{code-cell} ipython3
fig, axes = plt.subplots(1, 2, figsize=(12, 5))

# Capital per worker
axes[0].plot(k, linewidth=2)
axes[0].axhline(k_star, color='r', linestyle='--', label='Steady state $k^*$')
axes[0].set_xlabel('Time')
axes[0].set_ylabel('Capital per worker $k_t$')
axes[0].set_title('Transition to Steady State')
axes[0].legend()

# Output per worker
y = A * k ** α
axes[1].plot(y, linewidth=2, color='green')
axes[1].axhline(y_star, color='r', linestyle='--', label='Steady state $y^*$')
axes[1].set_xlabel('Time')
axes[1].set_ylabel('Output per worker $y_t$')
axes[1].set_title('Output Dynamics')
axes[1].legend()

plt.tight_layout()
plt.show()
```

## Comparative Statics

We can examine how changes in the savings rate affect the steady state.

```{code-cell} ipython3
s_values = np.linspace(0.05, 0.50, 100)
k_stars = (s_values * A / (δ + n)) ** (1 / (1 - α))
y_stars = A * k_stars ** α
c_stars = (1 - s_values) * y_stars

fig, ax = plt.subplots(figsize=(8, 5))
ax.plot(s_values, c_stars, linewidth=2, label='Consumption $c^*$')
ax.axvline(α, color='r', linestyle='--', label=f'Golden rule $s^* = \\alpha = {α}$')
ax.set_xlabel('Savings rate $s$')
ax.set_ylabel('Steady-state consumption per worker')
ax.set_title('Golden Rule of Capital Accumulation')
ax.legend()
plt.show()
```

## Exercises

```{exercise}
:label: solow_ex_a
```

Consider two economies, A and B, with the following parameters:
- Economy A: $s = 0.20$, $\delta = 0.05$, $n = 0.01$, $\alpha = 0.33$
- Economy B: $s = 0.35$, $\delta = 0.08$, $n = 0.03$, $\alpha = 0.33$

1. Calculate the steady-state capital and output per worker for each economy.
2. Which economy has higher steady-state consumption per worker?
3. Plot the transition dynamics for both economies starting from $k_0 = 1$.

```{exercise-end}
```

```{solution-start} solow_ex_a
:class: dropdown
```

```{code-cell} ipython3
for name, params in [('A', (0.20, 0.05, 0.01)), ('B', (0.35, 0.08, 0.03))]:
    s_i, δ_i, n_i = params
    k_i = (s_i * A / (δ_i + n_i)) ** (1 / (1 - α))
    y_i = A * k_i ** α
    c_i = (1 - s_i) * y_i
    print(f"Economy {name}: k* = {k_i:.4f}, y* = {y_i:.4f}, c* = {c_i:.4f}")
```

Economy A has higher steady-state consumption per worker despite its lower savings rate.

```{solution-end}
```
