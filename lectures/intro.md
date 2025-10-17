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

Economics is the study of how societies allocate scarce resources.

### Key Terms

- **Scarcity**: Limited resources
- **Opportunity cost**: The value of the next best alternative
- **Supply and demand**: Market forces that determine prices

## Economic Models

Economic models are simplified representations of reality used to understand and predict economic behavior.

### The Cobb-Douglas Model

One of the most fundamental models in economics is the Cobb-Douglas production function, which describes how inputs are transformed into outputs.

The model assumes that output depends on two main inputs:
- Capital (K): Physical assets like machinery and buildings
- Labor (L): Human effort and skills

### Key Properties

The Cobb-Douglas function exhibits several important economic properties:

1. **Constant returns to scale**: Doubling both inputs doubles output
2. **Diminishing marginal returns**: Each additional unit of input produces less additional output
3. **Substitutability**: Capital and labor can partially substitute for each other

These properties make the model particularly useful for analyzing long-run economic growth and resource allocation decisions.

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

# Example usage
gdp = calculate_gdp(capital=100, labor=50)
print(f"GDP: {gdp:.2f}")
```

## MyST Directives

```{note}
This is an important note about economic theory.
```

```{warning}
Be careful with assumptions in economic models!
```

```{tip}
Always verify your model's predictions against real data.
```

## Summary

This lecture introduced:
- Basic economic concepts (scarcity, opportunity cost, supply and demand)
- Economic models and the Cobb-Douglas production function
- Mathematical and computational applications

Understanding these fundamentals is essential for further study in economics.

## References

1. Cobb, C. W., & Douglas, P. H. (1928). A theory of production. *American Economic Review*, 18(1), 139-165.
2. Solow, R. M. (1956). A contribution to the theory of economic growth. *Quarterly Journal of Economics*, 70(1), 65-94.
