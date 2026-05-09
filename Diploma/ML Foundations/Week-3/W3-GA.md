# Core Concepts:

1.  **Vector Length (Norm):** $\|x\| = \sqrt{x_1^2 + x_2^2 + \dots + x_d^2}$.
2.  **Inner Product (Dot Product):** $x^T y = \sum x_i y_i$. If the result is **0**, the vectors are **Orthogonal (Perpendicular)**.
3.  **Rank-Nullity Theorem:** For a matrix with $n$ columns: **Rank + Nullity = $n$**.
    *   *Rank:* Number of independent columns.
    *   *Nullity:* Dimension of the Null Space ($Ax = 0$).
4.  **Projections onto a Line (Vector $a$):**
    *   **The Scalar ($\hat{x}$):** $\hat{x} = \frac{a^T b}{a^T a}$.
    *   **The Projection Vector ($p$):** $p = \hat{x} a$.
    *   **The Projection Matrix ($P$):** $P = \frac{a a^T}{a^T a}$.
5.  **Normal Equation (Least Squares):** To find the best fit $\hat{\theta}$ for $A\theta = b$, solve: $A^T A \hat{\theta} = A^T b$.

---

# Graded Assignment:

### Question 1: Vector Length
**Q:** The length of the vector $[1, 2, -1]^T$ is:
*   **Step 1:** Square each number: $1^2 = 1, 2^2 = 4, (-1)^2 = 1$.
*   **Step 2:** Add them up: $1 + 4 + 1 = 6$.
*   **Step 3:** Take the square root: $\sqrt{6} \approx 2.449$.
**Answer:** 2.449

### Question 2: Inner Product
**Q:** The inner product of $[1, 2, 3]^T$ and $[-1, 1, 5]^T$ is:
*   **Step 1:** Multiply matching pairs: $(1 \times -1), (2 \times 1), (3 \times 5)$.
*   **Step 2:** Add them: $-1 + 2 + 15 = 16$.
**Answer:** 16

### Question 3: Rank-Nullity Rule
**Q:** The rank of a $4 \times 3$ matrix is 1. What is the dimension of its null space?
*   **Exam Hack:** $n$ is the number of columns. Here, $n = 3$.
*   **Formula:** $\text{Nullity} = n - \text{Rank} = 3 - 1 = 2$.
**Answer:** 2

### Question 4: Orthogonality Test
**Q:** Which vector is orthogonal to $[1, -1, 3]^T$?
*   **Exam Hack:** Perpendicular means the dot product must be **0**.
*   **Test Option 4:** $[-3, 0, 1] \cdot [1, -1, 3] = (-3 \times 1) + (0 \times -1) + (1 \times 3) = -3 + 0 + 3 = 0$.
**Answer:** $[-3, 0, 1]$

### Question 5: Finding Matrix Rank
**Q:** Find the rank of matrix $A = [[1, 2, 3], [2, 4, 6], [3, 6, 9]]$.
*   **Concept:** Rank is the number of *unique* rows.
*   **Observation:** Row 2 is just Row 1 $\times 2$. Row 3 is just Row 1 $\times 3$. 
*   **Conclusion:** There is only 1 unique row.
**Answer:** 1

### Question 6: Subspace Rules
**Q:** What is the smallest subspace containing the first quadrant of $\mathbb{R}^2$?
*   **Concept:** A subspace must be closed under scalar multiplication (including negative numbers).
*   **Logic:** If you have a vector in the first quadrant and multiply it by $-1$, it lands in the third quadrant. To be a true "subspace," you eventually need the whole plane.
**Answer:** The whole space $\mathbb{R}^2$.

### Question 7: Practical Rank
**Q:** 5 peaches and 6 oranges cost 150. 10 peaches and 12 oranges cost 300. Rank?
*   **Logic:** Equation 2 is just Equation 1 $\times 2$. They are the same "information".
**Answer:** Rank = 1

### Question 8: Least Squares Regression
**Q:** Observations: $((1, 6), (-1, 3), (3, 15))$. Find least squares solution $\hat{\theta} = (a, b)$ for $y = ax + b$.
*   **Step 1:** Build $A$ (x-values in col 1, 1s in col 2) and $b$ (y-values).
    $A = \begin{bmatrix} 1 & 1 \\ -1 & 1 \\ 3 & 1 \end{bmatrix}, b = \begin{bmatrix} 6 \\ 3 \\ 15 \end{bmatrix}$
*   **Step 2:** Solve $A^T A \hat{\theta} = A^T b$.
    $A^T A = \begin{bmatrix} 11 & 3 \\ 3 & 3 \end{bmatrix}, A^T b = \begin{bmatrix} 48 \\ 24 \end{bmatrix}$.
*   **Step 3:** Solve the system: $11a + 3b = 48$ and $3a + 3b = 24$.
    Subtracting gives $8a = 24 \implies a = 3$. Then $3(3) + 3b = 24 \implies 3b = 15 \implies b = 5$.
**Answer:** (3, 5)

### Question 11: Projection onto a Line
**Q:** Find projection of $b = [5, -4, 1]$ along $a = [3, -2, 4]$.
*   **Step 1 ($a^T b$):** $(3 \times 5) + (-2 \times -4) + (4 \times 1) = 15 + 8 + 4 = 27$.
*   **Step 2 ($a^T a$):** $3^2 + (-2)^2 + 4^2 = 9 + 4 + 16 = 29$.
*   **Step 3 ($p$):** $\frac{27}{29} \times [3, -2, 4] = [\frac{81}{29}, \frac{-54}{29}, \frac{108}{29}]$.
**Answer:** $[\frac{81}{29}, \frac{-54}{29}, \frac{108}{29}]$

### Question 12: Projection Matrix
**Q:** The projection matrix for $v = [2, 1, 3]^T$ is:
*   **Step 1 ($v v^T$):** Create the grid: $\begin{bmatrix} 2 \\ 1 \\ 3 \end{bmatrix} \begin{bmatrix} 2 & 1 & 3 \end{bmatrix} = \begin{bmatrix} 4 & 2 & 6 \\ 2 & 1 & 3 \\ 6 & 3 & 9 \end{bmatrix}$.
*   **Step 2 ($v^T v$):** Sum of squares: $4 + 1 + 9 = 14$.
*   **Step 3 ($P$):** $\frac{1}{14} \times \text{Matrix}$.
**Answer:** Option 1

### Question 13: Projection (Practice)
**Q:** Find projection of $[2, -4, 4]$ along $[2, -2, 1]$.
*   **Dot Product ($a^T b$):** $(2 \times 2) + (-2 \times -4) + (1 \times 4) = 4 + 8 + 4 = 16$.
*   **Length Squared ($a^T a$):** $2^2 + (-2)^2 + 1^2 = 4 + 4 + 1 = 9$.
*   **Final:** $\frac{16}{9} \times [2, -2, 1] = [\frac{32}{9}, \frac{-32}{9}, \frac{16}{9}]$.
**Answer:** $[\frac{32}{9}, \frac{-32}{9}, \frac{16}{9}]$
