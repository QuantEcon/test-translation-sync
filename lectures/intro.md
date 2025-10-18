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

This is a comprehensive test lecture for the translation sync action, demonstrating various types of changes.

## Basic Concepts

Economics is the study of how societies allocate scarce resources among competing uses. It examines decision-making under constraints.

### Key Terms

- **Scarcity**: Limited resources relative to unlimited wants
- **Opportunity cost**: The value of the next best alternative foregone
- **Supply and demand**: Market forces that determine prices and quantities
- **Marginal analysis**: Examining incremental changes in costs and benefits

### Economic Systems

Different societies organize economic activity in various ways:
- Market economies rely on price signals
- Planned economies use central coordination
- Mixed economies combine both approaches

## Mathematical Framework

The production function represents the relationship between inputs and output:

$$
Y = A K^{\alpha} L^{1-\alpha}
$$

where:
- $Y$ is total output
- $K$ is capital stock
- $L$ is labor input
- $A$ is total factor productivity
- $\alpha \in (0,1)$ is the capital share parameter

### Returns to Scale

The Cobb-Douglas function exhibits constant returns to scale:

$$
F(\lambda K, \lambda L) = \lambda F(K, L)
$$

for any $\lambda > 0$.

## Python Implementation

Here's an improved implementation with additional features:

```python
import numpy as np

def calculate_gdp(capital, labor, productivity=1.0, alpha=0.3):
    """
    Calculate GDP using Cobb-Douglas production function
    
    Parameters:
    -----------
    capital : float
        Capital stock (K)
    labor : float
        Labor force (L)
    productivity : float
        Total factor productivity (A), default: 1.0
    alpha : float
        Capital share parameter, default: 0.3
        
    Returns:
    --------
    float : Calculated GDP (Y)
    
    Examples:
    ---------
    >>> calculate_gdp(100, 50)
    31.62
    """
    if capital < 0 or labor < 0:
        raise ValueError("Inputs must be non-negative")
    
    return productivity * (capital ** alpha) * (labor ** (1 - alpha))

def marginal_product_capital(capital, labor, productivity=1.0, alpha=0.3):
    """Calculate marginal product of capital"""
    return alpha * productivity * (capital ** (alpha - 1)) * (labor ** (1 - alpha))

# Example usage with multiple scenarios
scenarios = [
    {'capital': 100, 'labor': 50},
    {'capital': 150, 'labor': 75},
    {'capital': 200, 'labor': 100}
]

for i, scenario in enumerate(scenarios, 1):
    gdp = calculate_gdp(**scenario)
    mpk = marginal_product_capital(**scenario)
    print(f"Scenario {i}: GDP = {gdp:.2f}, MPK = {mpk:.4f}")
```

## Economic Applications

Let's explore some practical applications of these concepts.

### Labor Market Analysis

The labor market equilibrium occurs where labor supply equals labor demand. Wages adjust to clear the market.

### Capital Accumulation

Capital accumulation follows the law of motion:

$$
K_{t+1} = I_t + (1-\delta)K_t
$$

where $I_t$ is investment and $\delta$ is the depreciation rate.

## MyST Directives

```{note}
This is an important note about economic theory and its applications in real-world policy.
```

```{warning}
Be careful with assumptions in economic models! Always check robustness.
```

```{tip}
Always verify your model's predictions against real data before drawing policy conclusions.
```

```{admonition} Key Insight
The production function framework is fundamental to understanding economic growth and development.
```

## Empirical Evidence

Recent empirical studies have shown that total factor productivity accounts for a large fraction of cross-country income differences.

### Data Sources

Common data sources for empirical analysis include:
- Penn World Tables
- World Bank Development Indicators
- OECD National Accounts

## Summary

This lecture covered:
1. Basic economic concepts and terminology
2. Mathematical production functions and their properties
3. Computational methods for economic analysis
4. Practical applications in labor and capital markets
5. Empirical evidence and data sources

## References

- Smith, Adam. "The Wealth of Nations" (1776)
- Keynes, John Maynard. "The General Theory of Employment, Interest and Money" (1936)
- Solow, Robert M. "A Contribution to the Theory of Economic Growth" (1956)
- Romer, David. "Advanced Macroeconomics" (4th ed., 2019)
- Acemoglu, Daron and Robinson, James. "Why Nations Fail" (2012)
