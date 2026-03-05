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

The Solow growth model is one of the most important models in macroeconomics. It explains long-run economic growth through capital accumulation, labor growth, and technological progress.

## The Production Function

The economy produces output using a production function:

$$
Y = K^\alpha L^{1-\alpha}
$$

where $Y$ is output, $K$ is capital, $L$ is labor, and $\alpha$ is the capital share.

## Capital Accumulation

Capital evolves over time according to:

$$
K_{t+1} = sY_t + (1-\delta)K_t
$$

where $s$ is the savings rate and $\delta$ is the depreciation rate.

The model predicts that economies converge to a steady state where capital per worker is constant.

## Steady State

In the steady state, output per worker is:

$$
y^* = \left(\frac{s}{\delta}\right)^{\frac{\alpha}{1-\alpha}}
$$

This means higher savings rates lead to higher steady-state output per worker.

```{code-cell} python3
import numpy as np
import matplotlib.pyplot as plt

# Parameters
alpha = 0.3
s = 0.2
delta = 0.05
n = 0.02

# Compute steady state
k_star = (s / delta) ** (1 / (1 - alpha))
y_star = k_star ** alpha

print(f"Steady state capital: {k_star:.2f}")
print(f"Steady state output: {y_star:.2f}")
```

## Convergence Dynamics

Economies below the steady state grow faster than economies above it. This implies convergence across countries with similar parameters.
