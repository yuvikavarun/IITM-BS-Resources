# Notes from Mock
## Table of Contents
1. [Machine Learning Fundamentals](#1-machine-learning-fundamentals) ~17%
2. [Multivariable Calculus](#2-multivariable-calculus) ~11%
3. [Linear Algebra](#3-linear-algebra) ~11%
4. [Optimization](#4-optimization ~33%
5. [Probability & Statistics](#5-probability--statistics) ~28%

---

## 1. Machine Learning & Algorithm Fundamentals

### 1.1 Supervised vs. Unsupervised Learning
* **Supervised Learning:** Training a model on **labeled** data. You have the input data AND the correct answers (e.g., training a model on images that users have already flagged as "Violent").
* **Unsupervised Learning:** Training a model on **unlabeled** data to find hidden patterns or underlying structures (e.g., Density Estimation, clustering).

### 1.2 Classification vs. Regression
* **Classification:** Predicting discrete, categorical labels (e.g., Violent vs. Non-Violent).
* **Regression:** Predicting continuous, numerical values (e.g., predicting exact housing prices).

### 1.3 Mean Sum of Squared Residuals (MSE)
Used to evaluate the accuracy of a regression line (line of best fit).
* **Residual:** The vertical distance between an actual data point and the line's prediction ($y_{actual} - y_{predicted}$).
* **MSE Formula:** Add up all the squared residuals and divide by the number of points ($n$). Squaring them heavily penalizes large errors and prevents negative errors from canceling positive ones.
  $$MSE = \frac{1}{n} \sum_{i=1}^n (y_i - \hat{y}_i)^2$$

### 1.4 Gradient Descent
An iterative optimization algorithm used to find the local minimum of a differentiable function.
* **Intuition:** Imagine being blindfolded on a mountain; you feel the slope with your foot (derivative) and take a step downward.
* **Master Formula:** $$x_{n+1} = x_n - \eta \cdot f'(x_n)$$
  * $x_n$: Current position
  * $\eta$: Learning rate (step size multiplier)
  * $f'(x_n)$: The gradient/derivative evaluated at your current position.

---

## 2. Multivariable Calculus & Optimization

### 2.1 Gradients and Tangent Planes
* **Gradient Vector ($\nabla f$):** A vector pointing in the direction of the steepest slope, perfectly orthogonal (normal) to the surface at a given point.
  * **Formula:** $\nabla f(x, y, z) = \langle \frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, \frac{\partial f}{\partial z} \rangle$
* **Notation:** Parentheses $(x,y,z)$ represent a static point/location. Pointy brackets $\langle x,y,z \rangle$ represent a vector/directional arrow.
* **Tangent Plane Equation:** $$a(x - x_0) + b(y - y_0) + c(z - z_0) = 0$$
  * Where $\langle a,b,c \rangle$ is the gradient vector evaluated at point $(x_0, y_0, z_0)$.

### 2.2 Local Extrema & The Second Derivative Test
To classify a critical point (where slopes $f_x = 0$ and $f_y = 0$), use the Discriminant ($D$) built from second derivatives:
* **Discriminant Formula:** $D = f_{xx}f_{yy} - (f_{xy})^2$
* **Clairaut's Theorem:** For smooth functions, mixed partial derivatives are identical ($f_{xy} = f_{yx}$). This allows us to just square $f_{xy}$ in the formula above.
* **Classification Rules:**
  * **Saddle Point:** If $D < 0$ (Curves up one way, down the other).
  * **Local Minima:** If $D > 0$ AND $f_{xx} > 0$ (Concave UP / Bowl shape).
  * **Local Maxima:** If $D > 0$ AND $f_{xx} < 0$ (Concave DOWN / Dome shape).

### 2.3 Karush-Kuhn-Tucker (KKT) Conditions
Used for optimizing (minimizing/maximizing) a function subject to inequality constraints.
1. **Standardize:** Ensure constraints are in $g(x) \le 0$ format.
2. **Find Active Constraints:** Test the unconstrained minimum of your objective function. If it violates a constraint, that constraint is "active" and becomes a strict equality ($g(x) = 0$).
3. **The Lagrangian Gradient Equation:** At the optimal boundary point, the gradient of the function and the gradient of the active constraint are parallel.
   $$\nabla f(x) + \lambda \nabla g(x) = 0$$
4. **Solve:** Solve the resulting system of linear equations to find the optimal coordinates.

---

## 3. Linear Algebra

### 3.1 Eigenvalues ($\lambda$) & Eigenvectors ($v$)
* **The Shortcut:** For Upper Triangular matrices (zeros below the diagonal) or Diagonal matrices (zeros everywhere except the diagonal), the **eigenvalues are simply the numbers on the main diagonal**.
* **Finding Eigenvectors:** Solve the system $(A - \lambda I)v = 0$. 
* **Free Variables:** The number of free variables in the resulting system dictates how many linearly independent eigenvectors you get for that specific eigenvalue.

### 3.2 Matrix Definiteness & Surface Geometry (The Hessian)
The Hessian matrix ($H$) is a matrix of second derivatives $\begin{bmatrix} f_{xx} & f_{xy} \\ f_{yx} & f_{yy} \end{bmatrix}$. Its "definiteness" determines the global shape of the function based on the signs of its eigenvalues:
* **Positive Definite:** ALL eigenvalues $> 0$. The function is strictly **Convex** (upward bowl) for all real numbers.
* **Positive Semidefinite:** ALL eigenvalues $\ge 0$. Function is Convex, but may have flat valleys.
* **Negative Definite:** ALL eigenvalues $< 0$. The function is strictly **Concave** (downward dome) for all real numbers.
* **Negative Semidefinite:** ALL eigenvalues $\le 0$. Function is Concave, but may have flat ridges.
* **Indefinite:** Mix of positive and negative eigenvalues. The function forms a **Saddle** (neither strictly convex nor concave).

---

## 4. Probability & Statistics

### 4.1 Discrete Random Variables
* **Core Rule:** The sum of all probabilities in a sample space must equal exactly 1. ($\sum P(X=x) = 1$)
* **Expected Value (Mean):** Multiply every possible outcome by its probability, and sum them up.
  $$E(X) = \sum [x \cdot P(X=x)]$$

### 4.2 Conditional Probability ($A \mid B$)
* The vertical bar `|` means "given that."
* **Rule of Thumb:** The event on the right side of the bar is no longer a probability—it is a locked-in, 100% certain reality. Only calculate the odds of the remaining variables, treating the "given" condition as an absolute fact.

### 4.3 Linear Transformations of Normal Variables
When creating new variables $X = c_1Z_1 + c_2Z_2$ from standard normal variables $Z \sim \mathcal{N}(0,1)$:
1. **Mean Vector ($\mu$):** Because the mean of standard $Z$ is $0$, plug $0$ in for all $Z$ variables. The remaining constants form the mean vector.
2. **Transformation Matrix ($A$):** Extract the coefficients attached to the $Z$ variables into a matrix.
3. **Covariance Matrix ($\Sigma$):** Calculate $A$ multiplied by its transpose.
   $$\Sigma_X = A \cdot A^T$$

### 4.4 Bivariate Transformations (Jacobian Method)
Used to find the joint Probability Density Function (PDF) of new variables $Y_1, Y_2$ created from $X_1, X_2$.
1. **Joint PDF:** If $X_1, X_2$ are independent, multiply their PDFs together: $f(x_1, x_2) = f(x_1)f(x_2)$.
2. **Inverse Equations:** Solve for $X_1$ and $X_2$ in terms of $Y_1$ and $Y_2$.
3. **Jacobian Determinant ($J$):** Build a $2 \times 2$ matrix of the partial derivatives ($\frac{\partial X}{\partial Y}$) and find the determinant ($ad - bc$).
4. **Master Formula:** $$g(y_1, y_2) = f(x_1, x_2) \cdot |J|$$

### 4.5 Maximum Likelihood Estimation (MLE)
An optimization method to find the parameter ($\theta$) that makes your observed data the most likely.

**The Unitary Sample Case ($n=1$):**
1. Likelihood is just the PDF: $L(\theta) = f(x \mid \theta)$
2. Take the Natural Log: $l(\theta) = \ln[f(x \mid \theta)]$
3. Derivative to Zero: $\frac{d}{d\theta} l(\theta) = 0$
4. Solve for $\theta$.

**The Generalized Case ($n$ samples):**
Instead of just one data point, you have a dataset of $n$ independent observations ($x_1, x_2, ... x_n$).
1. **Likelihood Function ($L$):** Multiply the PDFs of all $n$ data points together using Product notation ($\prod$).
   $$L(\theta) = \prod_{i=1}^n f(x_i \mid \theta)$$
2. **Log-Likelihood ($l$):** Taking the natural log converts the massive multiplication into simple addition/summation ($\sum$).
   $$l(\theta) = \sum_{i=1}^n \ln[f(x_i \mid \theta)]$$
3. **Derivative to Zero:** Take the derivative with respect to $\theta$ and set it to 0.
4. **Solve for $\theta$:** The result is the global MLE formula for your parameter across any dataset size.
