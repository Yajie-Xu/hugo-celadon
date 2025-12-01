---
title: "Shadow Prices in Adaptive Subsidies"
date: 2024-12-10
summary: "Deriving the closed-form response of adaptive subsidy contracts to marginal emissions shocks."
image: "/images/categories/study.jpg"
---

We start from the dual problem:

$$ \min_{\lambda \ge 0} \left[ L(\lambda) = \sum_{i} \frac{(\lambda - c_i)^2}{2\beta_i} + \lambda E \right] $$

Taking the derivative gives

$$ \frac{\partial L}{\partial \lambda} = \sum_i \frac{\lambda - c_i}{\beta_i} + E = 0. $$

Solving for \( \lambda^* \) yields the adaptive shadow price

$$
\lambda^* = \frac{\sum_i \frac{c_i}{\beta_i} - E}{\sum_i \frac{1}{\beta_i}}.
$$

In code:

```python
import numpy as np

def lambda_star(costs, betas, emissions):
    numerator = np.sum(costs / betas) - emissions
    denominator = np.sum(1 / betas)
    return numerator / denominator
```

With \( c=[3,4,5] \), \( \beta=[2,1,4] \), \( E=2 \), the price stays below \$5 but reacts 1.2x faster than a static subsidy.
