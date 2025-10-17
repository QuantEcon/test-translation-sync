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

# Introduction to Economics

This is a comprehensive test lecture for the v0.4.1 translation sync action, designed to verify all bug fixes: proper section ordering, complete heading-map with subsections, no duplicates, and all sections present.

## Overview

This lecture provides a comprehensive introduction to economic principles and their computational applications.

### Core Principles

The study of economics rests on several fundamental pillars:

1. **Resource Allocation**: How societies decide what to produce
2. **Market Mechanisms**: The role of prices in coordinating decisions
3. **Optimization**: How agents make choices under constraints
4. **Equilibrium Analysis**: Understanding stable states in economic systems

## Basic Concepts

Economics is the study of how societies allocate scarce resources to satisfy unlimited wants and needs.

### Key Terms

- **Scarcity**: Limited resources relative to unlimited wants
- **Opportunity cost**: The value of the next best alternative foregone
- **Supply and demand**: Market forces that determine prices and quantities
- **Equilibrium**: A state where market forces are balanced

### Equilibrium

Market equilibrium occurs when quantity supplied equals quantity demanded, resulting in a stable price.

## Market Equilibrium

Market equilibrium is a fundamental concept in economic analysis.

### Equilibrium Conditions

For a market to be in equilibrium:
- Quantity demanded = Quantity supplied
- No tendency for price to change
- All agents are optimizing given prices

### Comparative Statics

Comparative statics analyzes how equilibrium changes when underlying parameters shift:
- Changes in consumer preferences
- Technological improvements
- Policy interventions

## Mathematical Example

The production function describes the relationship between inputs and output:

$$
Y = A K^{\alpha} L^{1-\alpha}
$$

where:
- $Y$ is output
- $K$ is capital  
- $L$ is labor
- $A$ is total factor productivity
- $\alpha$ is the capital share parameter

### Returns to Scale

This Cobb-Douglas production function exhibits constant returns to scale:

$$
F(tK, tL) = A(tK)^{\alpha}(tL)^{1-\alpha} = t \cdot AK^{\alpha}L^{1-\alpha} = tF(K,L)
$$

## Code Example

```python
import numpy as np
import matplotlib.pyplot as plt

def calculate_gdp(capital, labor, productivity=1.0, alpha=0.3):
    """
    Calculate GDP using Cobb-Douglas production function
    
    Parameters:
    -----------
    capital : float
        Capital stock
    labor : float
        Labor force
    productivity : float
        Total factor productivity (default: 1.0)
    alpha : float
        Capital share (default: 0.3)
        
    Returns:
    --------
    float : Calculated GDP
    """
    return productivity * (capital ** alpha) * (labor ** (1 - alpha))

# Example usage with visualization
capital_range = np.linspace(10, 200, 50)
gdp_values = [calculate_gdp(k, labor=50) for k in capital_range]

plt.figure(figsize=(10, 6))
plt.plot(capital_range, gdp_values, 'b-', linewidth=2)
plt.xlabel('Capital Stock')
plt.ylabel('GDP')
plt.title('Production Function: GDP vs Capital')
plt.grid(True, alpha=0.3)
plt.show()

print(f"GDP at K=100: {calculate_gdp(capital=100, labor=50):.2f}")
```

## MyST Directives

```{note}
This is an important note about economic theory and its applications.
```

```{warning}
Be careful with assumptions in economic models!
```

```{tip}
Always verify your model's predictions against real data.
```

```{important}
Understanding equilibrium concepts is crucial for economic analysis.
```

## Empirical Applications

Economic theory must be validated through empirical analysis.

### Data Analysis

Modern economics relies heavily on statistical methods to test theoretical predictions:
- Regression analysis
- Time series methods
- Panel data techniques

### Computational Methods

Numerical methods are essential when analytical solutions are unavailable:
- Optimization algorithms
- Monte Carlo simulation
- Dynamic programming

## Summary

This lecture covered essential topics in economics:

1. Fundamental economic concepts and resource allocation
2. Market equilibrium and comparative statics
3. Production functions and returns to scale
4. Computational methods for economic analysis
5. Empirical applications and data analysis

These concepts form the foundation for more advanced topics in economic theory and quantitative analysis.

## Exercises

Test your understanding with these exercises:

### Problem 1

Given a production function $Y = K^{0.3}L^{0.7}$ with $K=100$ and $L=50$:
1. Calculate output $Y$
2. Find the marginal product of capital
3. Verify constant returns to scale

### Problem 2

Using the code example above:
1. Modify the function to allow variable returns to scale
2. Plot GDP for different values of $\alpha$
3. Analyze the impact on capital's share of output

### Problem 3

Consider a market with demand $Q_d = 100 - 2P$ and supply $Q_s = 20 + 3P$:
1. Find the equilibrium price and quantity
2. Calculate consumer and producer surplus
3. Analyze the effect of a \$5 tax

## References

- Smith, Adam. "The Wealth of Nations" (1776)
- Keynes, John Maynard. "The General Theory of Employment, Interest and Money" (1936)
- Solow, Robert M. "A Contribution to the Theory of Economic Growth" (1956)
- Acemoglu, Daron. "Introduction to Modern Economic Growth" (2009)
- Stachurski, John and Sargent, Thomas J. "Quantitative Economics with Python" (2022)

## Further Reading

For deeper exploration of these topics:

- Advanced microeconomic theory
- Dynamic optimization methods
- Computational economics
- Econometric methods
- Modern macroeconomic theory
