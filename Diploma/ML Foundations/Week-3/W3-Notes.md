# Core Concepts:

1. **The Four Fundamental Subspaces:** Every matrix $A$ (with $m$ rows and $n$ columns) has four "rooms" where its vectors live.
   * **Column Space $C(A)$:** All possible linear combinations of the columns.
   * **Null Space $N(A)$:** All vectors $x$ that make $Ax = 0$.
   * **Row Space $R(A)$:** All possible linear combinations of the rows. 
   * **Left Null Space $N(A^T)$:** All vectors $y$ that make $A^T y = 0$.
2. **Orthogonality ($90^\circ$ Rule):** Two vectors are orthogonal if their dot product is zero ($x^T y = 0$). 
   * *Exam Hack:* The Row Space and Null Space are ALWAYS orthogonal to each other. The Column Space and Left Null Space are ALWAYS orthogonal to each other.
3. **The "Unsolvable" Problem ($Ax = b$):** In the real world, data is noisy. The equation $Ax = b$ almost never has a perfect solution because $b$ doesn't fit perfectly in the Column Space of $A$.
4. **The Fix (Projections & Least Squares):** Since we can't hit $b$ exactly, we find the closest "shadow" of $b$ on our column space. This is called a **Projection**. 
   * To find the best estimate ($\hat{x}$), we use the magic **Normal Equation**: $A^T A \hat{x} = A^T b$.

---

## Lecture 1: The Four Subspaces & Rank

**The Setup:** You have an $m \times n$ matrix $A$.
* $m$ = number of rows (equations)
* $n$ = number of columns (variables)
* $r$ = Rank (number of independent columns, found via Gaussian Elimination pivots).

**The Dimension Rules (MEMORIZE THESE):**
1. **Dimension of $C(A)$ (Column Space) = $r$**.
2. **Dimension of $R(A)$ (Row Space) = $r$**. *(Notice Row Rank always equals Column Rank!)*
3. **Dimension of $N(A)$ (Null Space) = $n - r$**. *(This is called "Nullity").*
4. **Dimension of $N(A^T)$ (Left Null Space) = $m - r$**.

**The Rank-Nullity Theorem:**
Rank + Nullity = Number of Columns ($r + (n-r) = n$).
*Exam Hack:* If a question asks for the dimension of the Null Space, just find the rank (how many pivot columns there are) and subtract it from the total number of columns.

---

## Lecture 2: Orthogonality

**What is it?**
Orthogonal is just the fancy math word for "perpendicular" or "at a right angle."
* **Length of a vector:** $||x||^2 = x^T x = x_1^2 + x_2^2 + ... + x_n^2$
* **Orthogonality Test:** If $x^T y = 0$, they are orthogonal.

**Orthogonal Subspaces:**
If you take *any* vector from the Row Space, and multiply it by *any* vector in the Null Space, the answer is always 0. 
* $R(A) \perp N(A)$
* $C(A) \perp N(A^T)$

---

## Lecture 3: Projection onto a Line (1D)

**The Concept:** 
You have a line pointing in direction $a$, and a random point $b$ floating in space. You want to drop a perpendicular line from $b$ straight down to $a$. The point where it hits is the projection $p$.

**The Formulas:**
1. **The Scalar ($\hat{x}$):** How much do we stretch $a$ to reach $p$? 
   $$\hat{x} = \frac{a^T b}{a^T a}$$
2. **The Projection ($p$):** The actual point on the line. 
   $$p = \hat{x}a$$
3. **The Projection Matrix ($P$):** The matrix that forces *any* vector onto the line $a$.
   $$P = \frac{a a^T}{a^T a}$$ 
   *(Careful: numerator is matrix $aa^T$, denominator is scalar $a^Ta$)*

---

## Lecture 4: Projection onto a Subspace (ND) & Least Squares

This is the core of Machine Learning regression.

**The Problem:** $Ax = b$ is inconsistent (no solution).
**The Goal:** Minimize the squared error $||Ax - b||^2$.

**The Magic Normal Equation:**
Since the error vector ($e = b - Ax$) must be orthogonal to our column space, we multiply both sides by $A^T$ to set the error to 0. 
$$A^T A \hat{x} = A^T b$$

**How to solve Least Squares problems on the exam:**
1. You are given matrix $A$ and vector $b$.
2. Calculate $A^T A$ (This will be a square, symmetric matrix).
3. Calculate $A^T b$ (This will be a vector).
4. Solve the new, easy system of equations: $(A^T A)\hat{x} = (A^T b)$ to find your best parameters $\hat{x}$.

**The Big Projection Matrix ($P$):**
$$P = A(A^T A)^{-1}A^T$$
* **Properties of $P$:**
  * It is symmetric: $P^T = P$
  * Projecting twice does nothing new (Idempotent): $P^2 = P$
  * *Exam Hack:* If a question asks "Is matrix $X$ a projection matrix?", just square it. If $X^2 = X$, and it is symmetric, the answer is YES.

---

## Lecture 5 & Tutorials: Curve Fitting Workflow

If you are asked to "Find the line of best fit $y = mx + c$ for these data points":

**Step 1: Build Matrix $A$ and Vector $b$**
* Put all your $x$-coordinates in the first column of $A$.
* Put all $1$s in the second column of $A$ (this represents the constant offset $c$).
* Put all your $y$-coordinates into vector $b$.

**Step 2: Use the Normal Equation**
* Compute $A^T A$.
* Compute $A^T b$.
* Solve $(A^T A)\hat{\theta} = (A^T b)$. 
* Your answer $\hat{\theta}$ will be a vector containing $[m, c]$ (your slope and intercept).

**Step 3: Finding the Error**
* Calculate your projected points: $p = A\hat{\theta}$.
* The error vector is: $e = b - p$.
* The sum of squared errors is the length of that error vector: $||e||^2$.
