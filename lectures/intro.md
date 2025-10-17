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

This is a test lecture for translation sync action with debug logging for v0.4.3.

## Overview

This lecture provides a comprehensive introduction to economic principles, covering fundamental concepts, mathematical models, and computational approaches. We'll explore how economists analyze market behavior and make predictions using both theoretical and empirical methods.

### Core Principles

The study of economics rests on several foundational principles:

1. **Rationality**: Agents make decisions to maximize their utility
2. **Equilibrium**: Markets tend toward stable states
3. **Efficiency**: Resources are allocated to maximize social welfare

## Basic Concepts

Economics is the study of how societies allocate scarce resources among competing uses. This fundamental challenge requires understanding both individual decision-making and aggregate market outcomes.

### Key Terms

- **Scarcity**: Limited resources relative to unlimited wants
- **Opportunity cost**: The value of the next best alternative forgone
- **Supply and demand**: Market forces that determine prices and quantities
- **Marginal analysis**: Examining the effect of small changes

## Market Equilibrium

Markets reach equilibrium when supply equals demand. At this point, there is no tendency for prices or quantities to change.

### Equilibrium Conditions

The equilibrium price $p^*$ and quantity $q^*$ satisfy:

$$
Q_d(p^*) = Q_s(p^*) = q^*
$$

where $Q_d$ is quantity demanded and $Q_s$ is quantity supplied.

## Mathematical Example

The production function describes how inputs are transformed into outputs:

$$
Y = A K^{\alpha} L^{1-\alpha}
$$

where:
- $Y$ is output
- $K$ is capital stock
- $L$ is labor input
- $A$ is total factor productivity
- $\alpha$ is the capital share parameter

This Cobb-Douglas form exhibits constant returns to scale and diminishing marginal products.

## Code Example

```python
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

# Example usage with different scenarios
scenarios = [
    {"capital": 100, "labor": 50, "name": "Base case"},
    {"capital": 150, "labor": 50, "name": "High capital"},
    {"capital": 100, "labor": 75, "name": "High labor"}
]

for scenario in scenarios:
    gdp = calculate_gdp(scenario["capital"], scenario["labor"])
    print(f"{scenario['name']}: GDP = {gdp:.2f}")
```

## Policy Implications

Economic theory informs policy decisions across multiple domains:

1. **Monetary policy**: Central banks manage interest rates and money supply
2. **Fiscal policy**: Governments adjust spending and taxation
3. **Regulatory policy**: Rules shape market behavior and outcomes

### Policy Trade-offs

Policymakers must balance competing objectives:
- Growth vs. stability
- Efficiency vs. equity
- Short-run vs. long-run effects

## MyST Directives

```{note}
This is an important note about economic theory. Models are simplifications of reality and should be used with appropriate caution.
```

```{warning}
Be careful with assumptions in economic models! Small changes in assumptions can lead to dramatically different conclusions.
```

```{tip}
Always verify your model's predictions against real data. Empirical validation is essential for credible economic analysis.
```

## Exercises

Test your understanding with these exercises:

1. Calculate equilibrium price when $Q_d = 100 - 2p$ and $Q_s = 20 + 3p$
2. Show that the Cobb-Douglas function has constant returns to scale
3. Implement a supply-demand solver in Python

### Exercise Solutions

Solutions are available in the appendix and online repository.

## Summary

This lecture covered fundamental topics in economics:
1. Basic economic concepts and terminology
2. Market equilibrium and price determination
3. Production functions and returns to scale
4. Computational methods for economic analysis
5. Policy applications and trade-offs

Understanding these foundations is essential for further study in economics.

## References

- Smith, Adam. "The Wealth of Nations" (1776)
- Keynes, John Maynard. "The General Theory of Employment, Interest and Money" (1936)
- Solow, Robert M. "A Contribution to the Theory of Economic Growth" (1956)
- Mas-Colell, Andreu, Michael D. Whinston, and Jerry R. Green. "Microeconomic Theory" (1995)
