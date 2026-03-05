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

# The Solow Growth Model

This lecture introduces the Solow growth model, a foundational framework in macroeconomics for understanding long-run economic growth.

## Setup

The Solow model considers an economy with the following production function:

$$
Y = F(K, L) = K^\alpha L^{1-\alpha}
$$

where $Y$ is output, $K$ is capital, $L$ is labor, and $\alpha \in (0, 1)$ is the capital share of income.

In per-worker terms, output per worker $y = Y/L$ is:

$$
y = k^\alpha
$$

where $k = K/L$ is capital per worker.

```{code-cell} python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
alpha = 0.3    # capital share
s = 0.2        # savings rate
delta = 0.1    # depreciation rate
n = 0.02       # population growth rate

# Production function (per worker)
def output(k, alpha):
    return k ** alpha
```

## Capital Accumulation

The capital accumulation equation in per-worker terms is:

$$
\dot{k} = s \cdot k^\alpha - (n + \delta) \cdot k
$$

where $s$ is the savings rate, $\delta$ is the depreciation rate, and $n$ is the population growth rate.

```{code-cell} python
# Capital accumulation
def k_dot(k, s, alpha, n, delta):
    return s * output(k, alpha) - (n + delta) * k

# Plot capital accumulation
k_vals = np.linspace(0.1, 10, 100)
investment = s * output(k_vals, alpha)
breakeven = (n + delta) * k_vals

fig, ax = plt.subplots(figsize=(8, 5))
ax.plot(k_vals, investment, 'b-', linewidth=2, label='Investment: $s k^\\alpha$')
ax.plot(k_vals, breakeven, 'r-', linewidth=2, label='Break-even: $(n+\\delta) k$')
ax.set_xlabel('Capital per worker (k)', fontsize=12)
ax.set_ylabel('Investment / Break-even', fontsize=12)
ax.set_title('Solow Model: Capital Accumulation', fontsize=14)
ax.legend()
ax.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()
```

## Steady State

At the steady state, $\dot{k} = 0$, which gives:

$$
s \cdot (k^*)^\alpha = (n + \delta) \cdot k^*
$$

Solving for $k^*$:

$$
k^* = \left(\frac{s}{n + \delta}\right)^{\frac{1}{1-\alpha}}
$$

The corresponding steady-state output per worker is:

$$
y^* = \left(\frac{s}{n + \delta}\right)^{\frac{\alpha}{1-\alpha}}
$$

Note that the denominator includes the population growth rate $n$. This means higher savings rates lead to higher steady-state output per worker, while higher population growth rates reduce steady-state output per worker.

```{code-cell} python
# Compute steady state
k_star = (s / (n + delta)) ** (1 / (1 - alpha))
y_star = output(k_star, alpha)

print(f"Steady state capital per worker: {k_star:.2f}")
print(f"Steady state output per worker: {y_star:.2f}")
```

## Comparative Statics

How does steady-state output respond to changes in the savings rate?

```{code-cell} python
# Comparative statics: effect of savings rate
s_values = np.linspace(0.05, 0.5, 50)
y_star_values = (s_values / (n + delta)) ** (alpha / (1 - alpha))

fig, ax = plt.subplots(figsize=(8, 5))
ax.plot(s_values, y_star_values, 'b-', linewidth=2)
ax.set_xlabel('Savings rate (s)', fontsize=12)
ax.set_ylabel('Steady-state output per worker (y*)', fontsize=12)
ax.set_title('Effect of Savings Rate on Steady-State Output', fontsize=14)
ax.axvline(x=s, color='r', linestyle='--', label=f's = {s}')
ax.legend()
ax.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()
```
