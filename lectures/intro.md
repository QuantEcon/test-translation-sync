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

# Economic Growth Theory

This lecture introduces the Solow-Swan model of economic growth, examining how economies expand through capital accumulation and technological progress.

## Overview

Economic growth theory seeks to explain the sources of long-run increases in per capita income. The Solow-Swan model, developed independently by Robert Solow and Trevor Swan in 1956, remains one of the most influential frameworks in macroeconomics.

### Historical Context

The post-war period saw rapid economic recovery in many countries, raising questions about the drivers of growth. The Solow model provided a rigorous framework for understanding these dynamics.

### Learning Objectives

After completing this lecture, you will be able to:
- Understand the mechanics of capital accumulation
- Solve for steady-state equilibrium
- Analyze convergence dynamics
- Implement the model computationally

## The Production Function

Output is produced using capital $K_t$ and labor $L_t$ through a Cobb-Douglas production function:

$$
Y_t = A K_t^{\alpha} L_t^{1-\alpha}
$$

where $A > 0$ is total factor productivity and $\alpha \in (0,1)$ is capital's share of output.

### Properties

The production function satisfies several key properties.

#### Constant Returns to Scale

Doubling all inputs doubles output:

$$
F(2K, 2L) = 2F(K, L)
$$

#### Diminishing Marginal Returns

Each additional unit of capital produces less output:

$$
\frac{\partial^2 Y}{\partial K^2} < 0
$$

### Intensive Form

Defining per-worker variables $y = Y/L$ and $k = K/L$, we can write:

$$
y = A k^{\alpha}
$$

This simplifies our analysis considerably.

## Capital Accumulation

The capital stock evolves according to:

$$
K_{t+1} = sY_t + (1-\delta)K_t
$$

where $s \in (0,1)$ is the savings rate and $\delta \in (0,1)$ is the depreciation rate.

### Investment and Depreciation

Net investment equals gross investment minus depreciation:

$$
\Delta K = sY - \delta K
$$

In steady state, net investment equals zero.

### Per-Worker Dynamics

The law of motion for capital per worker is:

$$
k_{t+1} = sAk_t^{\alpha} + (1-\delta)k_t
$$

## Steady State Analysis

The economy converges to a steady state where capital per worker is constant.

### Steady State Capital

Setting $k_{t+1} = k_t = k^*$, we find:

$$
k^* = \left(\frac{sA}{\delta}\right)^{\frac{1}{1-\alpha}}
$$

### Steady State Output

Output per worker in steady state is:

$$
y^* = A(k^*)^{\alpha} = A^{\frac{1}{1-\alpha}}\left(\frac{s}{\delta}\right)^{\frac{\alpha}{1-\alpha}}
$$

### Stability

The steady state is globally stable. From any initial $k_0 > 0$, the economy converges to $k^*$.

## Python Implementation

Let's implement the Solow model in Python.

### Basic Setup

```python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
A = 2.0      # Total factor productivity
alpha = 0.3  # Capital share
s = 0.2      # Savings rate
delta = 0.1  # Depreciation rate
```

### Production Function

```python
def output(k, A=2.0, alpha=0.3):
    """
    Cobb-Douglas production function (intensive form)
    
    Parameters:
    -----------
    k : float or array
        Capital per worker
    A : float
        Total factor productivity
    alpha : float
        Capital share
        
    Returns:
    --------
    float or array : Output per worker
    """
    return A * k**alpha
```

### Capital Evolution

```python
def capital_next(k, s=0.2, delta=0.1, A=2.0, alpha=0.3):
    """
    Law of motion for capital per worker
    
    Parameters:
    -----------
    k : float
        Current capital per worker
    s : float
        Savings rate
    delta : float
        Depreciation rate
        
    Returns:
    --------
    float : Next period capital per worker
    """
    return s * output(k, A, alpha) + (1 - delta) * k
```

### Simulation

```python
def simulate_solow(k0, T=50, s=0.2, delta=0.1, A=2.0, alpha=0.3):
    """
    Simulate the Solow model
    
    Parameters:
    -----------
    k0 : float
        Initial capital per worker
    T : int
        Time horizon
        
    Returns:
    --------
    array : Path of capital per worker
    """
    k_path = np.empty(T)
    k_path[0] = k0
    
    for t in range(T-1):
        k_path[t+1] = capital_next(k_path[t], s, delta, A, alpha)
    
    return k_path
```

## Numerical Analysis

Let's examine the model's behavior numerically.

### Convergence to Steady State

```python
# Initial conditions
k0_low = 0.5
k0_high = 8.0

# Simulate
k_path_low = simulate_solow(k0_low)
k_path_high = simulate_solow(k0_high)

# Calculate steady state
k_star = (s * A / delta)**(1/(1-alpha))

# Plot
plt.figure(figsize=(10, 6))
plt.plot(k_path_low, label=f'Starting from k={k0_low}')
plt.plot(k_path_high, label=f'Starting from k={k0_high}')
plt.axhline(k_star, color='red', linestyle='--', label='Steady state')
plt.xlabel('Time')
plt.ylabel('Capital per worker')
plt.title('Convergence to Steady State')
plt.legend()
plt.grid(True)
plt.show()
```

### Comparative Statics

How do parameter changes affect the steady state?

#### Savings Rate

```python
s_values = np.linspace(0.1, 0.5, 20)
k_star_values = [(s_val * A / delta)**(1/(1-alpha)) for s_val in s_values]

plt.plot(s_values, k_star_values)
plt.xlabel('Savings rate (s)')
plt.ylabel('Steady-state capital')
plt.title('Effect of Savings Rate on Steady State')
plt.grid(True)
plt.show()
```

#### Productivity

```python
A_values = np.linspace(1.0, 3.0, 20)
k_star_A = [(s * A_val / delta)**(1/(1-alpha)) for A_val in A_values]

plt.plot(A_values, k_star_A)
plt.xlabel('TFP (A)')
plt.ylabel('Steady-state capital')
plt.title('Effect of Productivity on Steady State')
plt.grid(True)
plt.show()
```

## Policy Implications

The Solow model offers important insights for economic policy.

### The Golden Rule

The golden rule savings rate maximizes steady-state consumption per worker.

#### Derivation

Consumption per worker in steady state is:

$$
c^* = y^* - \delta k^* = A(k^*)^{\alpha} - \delta k^*
$$

Maximizing with respect to $k^*$ gives:

$$
\alpha A (k^*)^{\alpha-1} = \delta
$$

This implies:

$$
s_{gold} = \alpha
$$

### Growth vs. Levels

A key insight from the Solow model: changes in the savings rate affect the level of income but not the long-run growth rate. For sustained growth, we need technological progress.

## Extensions and Limitations

The basic Solow model has several important extensions.

### Population Growth

Adding population growth $n$ changes the steady state to:

$$
k^* = \left(\frac{sA}{n + \delta}\right)^{\frac{1}{1-\alpha}}
$$

### Technological Progress

Labor-augmenting technological progress at rate $g$ allows for sustained growth in per capita income.

### Limitations

The model treats savings and technological progress as exogenous, which limits its explanatory power for understanding why countries grow at different rates.

## Exercises

Test your understanding with these problems.

### Analytical Problems

1. Derive the steady-state capital stock for the case with population growth
2. Show that the golden rule savings rate is $s_{gold} = \alpha$
3. Prove that the steady state is globally stable

### Numerical Problems

1. Compute the transition path from $k_0 = 1$ to steady state
2. Calculate the half-life of convergence
3. Simulate the effect of a permanent increase in TFP

### Solutions

Selected solutions are available in the appendix.

## Summary

This lecture introduced the Solow-Swan growth model. Key takeaways:

- Capital accumulation drives short-run growth
- Economies converge to a unique steady state
- Savings affect levels but not long-run growth rates
- Technological progress is essential for sustained growth

### Further Reading

For deeper understanding, consult:
- Solow, Robert M. "A Contribution to the Theory of Economic Growth" (1956)
- Swan, Trevor W. "Economic Growth and Capital Accumulation" (1956)
- Barro and Sala-i-Martin. "Economic Growth" (2004)
- Acemoglu, Daron. "Introduction to Modern Economic Growth" (2009)
