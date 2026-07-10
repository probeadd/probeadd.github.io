---
layout: post
title: "It's a Sample Post"
date: 2026-07-09
tags: [python, math, data-science]
---

In this post, we will look at how to implement a basic linear gradient descent algorithm using Python, alongside the mathematical formulas that power it.

### 1. The Mathematics (LaTeX)

Linear regression models the relationship between a dependent variable and one or more independent variables. The foundational equation for a simple linear model is written as:

$$y = \beta_0 + \beta_1 x + \epsilon$$

Where:
* $$\beta_0$$ is the y-intercept.
* $$\beta_1$$ is the slope coefficient.
* $$\epsilon$$ represents the error term.

To find the best-fitting line, we minimize the **Mean Squared Error (MSE)** cost function, which is defined mathematically as:

$$J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2$$

---

### 2. The Implementation (Python Code)

Here is how you can write a simple Python function to calculate that exact Mean Squared Error using the `numpy` library.

```python
import numpy as np

def compute_cost(X, y, theta):
    """
    Compute the cost (MSE) for linear regression.

    Parameters:
    X : 2D array of features (m x n)
    y : 1D array of target values (m,)
    theta : 1D array of fitting parameters (n,)
    """
    m = len(y)
    predictions = X.dot(theta)
    errors = predictions - y
    sq_errors = np.square(errors)

    # Implementing the 1/(2m) * sum equation from above
    cost = (1 / (2 * m)) * np.sum(sq_errors)
    return cost

# Example usage:
# X_data = np.array([[1, 1], [1, 2], [1, 3]])
# y_data = np.array([1, 2, 3])
# theta_init = np.zeros(2)
# print(compute_cost(X_data, y_data, theta_init))
```
