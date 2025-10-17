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

This is a comprehensive test lecture for the translation sync action.

Updated introduction paragraph with more context about the field.

## Overview

Economic analysis helps us understand how individuals, businesses, and governments make decisions under conditions of scarcity.

### Core Principles

- **Rational choice**: Agents make decisions to maximize utility
- **Market mechanisms**: Prices coordinate economic activity
- **Incentives matter**: People respond to incentives in predictable ways

## Basic Concepts

Economics is the study of how societies allocate scarce resources to meet unlimited wants and needs.

### Key Terms

- **Scarcity**: Limited resources relative to unlimited wants
- **Opportunity cost**: The value of the next best alternative foregone
- **Supply and demand**: Market forces that determine prices in competitive markets
- **Marginal utility**: Additional satisfaction from consuming one more unit
- **Equilibrium**: State where supply equals demand

## Market Equilibrium

Market equilibrium occurs when supply equals demand at a particular price level.

### Equilibrium Conditions

The equilibrium price $P^*$ and quantity $Q^*$ satisfy:

$$
Q_d(P^*) = Q_s(P^*)
$$

where $Q_d$ is quantity demanded and $Q_s$ is quantity supplied.

### Comparative Statics

Changes in market conditions shift supply or demand curves:

- **Demand shifters**: Income, preferences, prices of related goods
- **Supply shifters**: Technology, input costs, number of sellers

When demand increases (shifts right), equilibrium price and quantity both rise.

## Mathematical Example

The production function:

$$
Y = A K^{\alpha} L^{1-\alpha}
$$

where:
- $Y$ is output
- $K$ is capital stock
- $L$ is labor force
- $A$ is total factor productivity (TFP)

### Returns to Scale

This Cobb-Douglas function exhibits constant returns to scale:

$$
F(tK, tL) = t \cdot F(K, L)
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
    capital : float or array
        Capital stock
    labor : float or array
        Labor force  
    productivity : float
        Total factor productivity (default: 1.0)
    alpha : float
        Capital share of output (default: 0.3)
        
    Returns:
    --------
    float or array
        Calculated GDP
    """
    return productivity * (capital ** alpha) * (labor ** (1 - alpha))

# Example usage with different capital levels
K_values = np.linspace(50, 150, 100)
L = 50
gdp_values = calculate_gdp(K_values, L)

# Visualize production function
plt.figure(figsize=(10, 6))
plt.plot(K_values, gdp_values, linewidth=2)
plt.xlabel('Capital (K)')
plt.ylabel('Output (Y)')
plt.title('Production Function: Y = f(K, L)')
plt.grid(True, alpha=0.3)
plt.show()

print(f"GDP at K=100: {calculate_gdp(100, 50):.2f}")
```

## MyST Directives

```{note}
This section demonstrates MyST-specific markdown extensions for enhanced documentation.
```

```{warning}
Economic models make simplifying assumptions. Always validate predictions against empirical data!
```

```{tip}
When building economic models, start simple and add complexity gradually.
```

```{important}
The Cobb-Douglas function is widely used but has limitations. Consider alternatives like CES functions.
```

## Empirical Applications

### Data Sources

Common data sources for economic analysis:

- **FRED**: Federal Reserve Economic Data
- **World Bank**: International development data
- **OECD**: Data from developed economies
- **BLS**: Bureau of Labor Statistics (US labor market data)

### Example Analysis

```python
# Simulate simple regression analysis
import pandas as pd
from sklearn.linear_model import LinearRegression

# Create sample data
data = pd.DataFrame({
    'capital': K_values,
    'output': gdp_values
})

# Fit log-linear model: log(Y) = α·log(K) + β
X = np.log(data[['capital']])
y = np.log(data['output'])

model = LinearRegression()
model.fit(X, y)

print(f"Estimated capital elasticity: {model.coef_[0]:.3f}")
```

## Summary

This lecture covered the following key topics:

1. **Core economic principles** - rational choice, market mechanisms, and incentives
2. **Basic concepts** - scarcity, opportunity cost, and market equilibrium  
3. **Market equilibrium** - equilibrium conditions and comparative statics
4. **Production functions** - Cobb-Douglas form and returns to scale
5. **Computational methods** - implementing economic models in Python with visualization
6. **Empirical applications** - data sources and regression analysis
7. **MyST markdown** - special directives for enhanced technical documentation

These fundamentals form the foundation for more advanced economic analysis.

## Exercises

### Problem 1: Production Function

Given $A = 2.0$, $\alpha = 0.4$, $K = 100$, and $L = 64$, calculate:

a) Total output $Y$
b) Marginal product of capital: $MPK = \frac{\partial Y}{\partial K}$
c) Marginal product of labor: $MPL = \frac{\partial Y}{\partial L}$

### Problem 2: Market Equilibrium

Find the equilibrium price and quantity for:
- Demand: $Q_d = 200 - 5P$
- Supply: $Q_s = 50 + 3P$

### Problem 3: Empirical Analysis

Using Python, download GDP and capital stock data from FRED and estimate the capital elasticity $\alpha$ using regression analysis.

## References

- Smith, Adam. "The Wealth of Nations" (1776)
- Keynes, John Maynard. "The General Theory of Employment, Interest and Money" (1936)
- Solow, Robert M. "A Contribution to the Theory of Economic Growth" (1956)
- Cobb, Charles W. and Douglas, Paul H. "A Theory of Production" (1928)
- Romer, David. "Advanced Macroeconomics" (5th ed., 2019)

## Further Reading

- Acemoglu, Daron. "Introduction to Modern Economic Growth" (2009)
- Mas-Colell, Andreu, et al. "Microeconomic Theory" (1995)
- Sargent, Thomas and Ljungqvist, Lars. "Recursive Macroeconomic Theory" (4th ed., 2018)
