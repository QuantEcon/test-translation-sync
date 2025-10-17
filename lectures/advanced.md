---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
---

# Advanced Economic Theory

This lecture covers more advanced topics in economic theory.

## Dynamic Programming

The Bellman equation for value iteration:

$$
V(s) = \max_{a \in A(s)} \left\{ r(s,a) + \beta \sum_{s' \in S} P(s'|s,a) V(s') \right\}
$$

where:
- $V(s)$ is the value function
- $s$ is the current state
- $a$ is the action
- $r(s,a)$ is the reward function
- $\beta$ is the discount factor
- $P(s'|s,a)$ is the transition probability

## Implementation

```python
import numpy as np

def value_iteration(reward, transition, beta=0.95, tol=1e-6, max_iter=1000):
    """
    Solve dynamic programming problem using value iteration
    
    Parameters:
    -----------
    reward : ndarray
        Reward matrix (n_states x n_actions)
    transition : ndarray  
        Transition probability matrix (n_states x n_actions x n_states)
    beta : float
        Discount factor (default: 0.95)
    tol : float
        Convergence tolerance (default: 1e-6)
    max_iter : int
        Maximum iterations (default: 1000)
        
    Returns:
    --------
    V : ndarray
        Optimal value function
    policy : ndarray
        Optimal policy
    """
    n_states, n_actions = reward.shape
    V = np.zeros(n_states)
    
    for iteration in range(max_iter):
        V_new = np.zeros(n_states)
        
        for s in range(n_states):
            q_values = reward[s] + beta * np.dot(transition[s], V)
            V_new[s] = np.max(q_values)
        
        if np.max(np.abs(V_new - V)) < tol:
            print(f"Converged in {iteration} iterations")
            break
            
        V = V_new
    
    # Extract optimal policy
    policy = np.zeros(n_states, dtype=int)
    for s in range(n_states):
        q_values = reward[s] + beta * np.dot(transition[s], V)
        policy[s] = np.argmax(q_values)
    
    return V, policy
```

## Applications

Dynamic programming is fundamental to:

1. **Optimal growth models** - Determining optimal savings and consumption
2. **Job search theory** - Finding optimal reservation wages  
3. **Asset pricing** - Valuing financial instruments
4. **Inventory management** - Optimizing stock levels

```{admonition} Key Insight
:class: important

Dynamic programming breaks complex sequential decision problems into simpler subproblems.
This "principle of optimality" is what makes DP so powerful.
```

## Computational Considerations

```{note}
Value iteration converges geometrically at rate $\beta$. Faster convergence can be achieved with:
- Policy iteration
- Modified policy iteration
- Linear programming methods
```
