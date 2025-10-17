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

This is a test lecture for translation sync action.

## Basic Concepts

Economics is the study of how societies allocate scarce resources to meet unlimited wants and needs.

### Key Terms

- **Scarcity**: Limited resources relative to unlimited wants
- **Opportunity cost**: The value of the next best alternative foregone
- **Supply and demand**: Market forces that determine prices in competitive markets
- **Marginal utility**: Additional satisfaction from consuming one more unit

## Market Equilibrium

Market equilibrium occurs when supply equals demand at a particular price level.

### Equilibrium Conditions

The equilibrium price $P^*$ and quantity $Q^*$ satisfy:

$$
Q_d(P^*) = Q_s(P^*)
$$

where $Q_d$ is quantity demanded and $Q_s$ is quantity supplied.

### Example

Consider a simple linear market:
- Demand: $Q_d = 100 - 2P$
- Supply: $Q_s = 20 + 3P$

Solving for equilibrium:
$$
100 - 2P^* = 20 + 3P^* \\
P^* = 16, \quad Q^* = 68
$$

## Mathematical Example

The production function:

$$
Y = A K^{\alpha} L^{1-\alpha}
$$

where:
- $Y$ is output
- $K$ is capital  
- $L$ is labor
- $A$ is total factor productivity

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
        Labor input
    productivity : float
        Total factor productivity (A)
    alpha : float
        Output elasticity of capital
        
    Returns:
    --------
    float
        GDP output
    """
    return productivity * (capital ** alpha) * (labor ** (1 - alpha))

# Example usage
gdp = calculate_gdp(capital=100, labor=50)
print(f"GDP: {gdp:.2f}")
```

## MyST Directives

```{note}
This section demonstrates MyST-specific markdown extensions.
```

```{warning}
Be careful with assumptions in economic models!
```

```{tip}
Always verify your model's predictions against real data.
```

## Summary

This lecture covered the following key topics:

1. **Basic economic concepts** - scarcity, opportunity cost, and market forces
2. **Market equilibrium** - where supply meets demand
3. **Production functions** - mathematical modeling of economic output
4. **Computational methods** - implementing economic models in Python
5. **MyST markdown** - special directives for enhanced documentation

These fundamentals form the foundation for more advanced economic analysis.

## References

- Smith, Adam. "The Wealth of Nations" (1776)
- Keynes, John Maynard. "The General Theory of Employment, Interest and Money" (1936)
- Solow, Robert M. "A Contribution to the Theory of Economic Growth" (1956)
