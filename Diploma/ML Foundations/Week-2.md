# Core Concepts:

1. **Vectors and the Dot Product:**
   * A vector is a direction and magnitude. `[2, 3]` means 2 steps East, 3 steps North.
   * **Dot Product ($x^T y$):** Multiplies matching parts and adds them up. 
   * **Orthogonal (Perpendicular):** If the dot product of two vectors equals **0**, they are perpendicular.
2. **Derivatives (1D vs Multivariate):**
   * **1D Derivative ($f'(x)$):** The slope of the tangent line. 
   * **Gradient ($\nabla f$):** The multivariate derivative. It's a vector containing all the partial derivatives. It always points in the direction of **Steepest Ascent**.
3. **The Gradient Hacks:**
   * **Steepest Ascent:** Move *with* the gradient $\rightarrow \nabla f$
   * **Steepest Descent:** Move *opposite* the gradient $\rightarrow -\nabla f$
   * **Perpendicularity:** The gradient is always perpendicular to contour lines.
4. **Linear Approximations:**
   * Formula: $L_v(x) = f(v) + \nabla f(v)^T(x - v)$
   * In English: `New Value = Old Value + (Slope * Step Size)`

---

# GA2

### Question 1: Continuity
**Q:** Which of the following functions is/are continuous? 
*Options: $\frac{1}{x-1}$, $\frac{x^2-1}{x-1}$, $sign(x-2)$, $\sin(x)$*
* **Concept:** Continuous means you can draw it without lifting your pen. 
* **Exam Hack:** Look for denominators. If the bottom can be $0$, there's a break in the curve. For the first two, $x=1$ causes division by zero. The `sign` function jumps suddenly from -1 to 1. 
* **Answer:** $\sin(x)$ (It's a smooth, endless wave).

### Question 2: Matrix vs Scalar
**Q:** Regarding a $d$-dimensional vector $x$, which of the following four options is not equivalent to the rest three options?
*Options: $x^T x$, $||x||^2$, $\sum x_i^2$, $x x^T$*
* **Concept:** The first three are just different ways to write the **Dot Product** (or squared length) of a vector with itself. The output is a *single number (scalar)*. 
* **Exam Hack:** $x x^T$ (column vector times row vector) creates a massive *grid of numbers (a Matrix)*. It is the odd one out.
* **Answer:** $x x^T$

### Question 3: Continuity & Differentiability
**Q:** Consider the piecewise function $f(x) = \{3x+3 \text{ if } x \ge 3; 2x+8 \text{ if } x < 3\}$. Which is true?
* **Concept:** Differentiable $\implies$ Continuous. If it's not continuous, it CANNOT be differentiable.
* **Step 1:** Plug $x=3$ into the top equation: $3(3) + 3 = 12$.
* **Step 2:** Plug $x=3$ into the bottom equation: $2(3) + 8 = 14$.
* **Conclusion:** $12 \neq 14$. The two halves of the function don't meet. It is broken (Not continuous), which automatically means it is Not differentiable.
* **Answers:** $f(x)$ is not continuous at $x=3$. $f(x)$ is not differentiable at $x=3$.

### Question 4: 1D Linear Approximation (Exponential)
**Q:** Approximate the value of $e^{0.011}$ by linearizing $e^x$ around $x=0$.
* **Concept:** `Estimate = Old Value + (Slope * Step)`
* **Step 1 (Old Value):** $f(0) = e^0 = 1$.
* **Step 2 (Slope):** The derivative of $e^x$ is $e^x$. At $x=0$, slope $= e^0 = 1$.
* **Step 3 (Step Size):** We moved from $0$ to $0.011$. Step $= 0.011$.
* **Step 4 (Math):** Estimate $= 1 + (1 * 0.011) = 1.011$.
* **Answer:** $1.011$

### Question 5: 1D Linear Approximation (Square Root)
**Q:** Approximate $\sqrt{3.9}$ by linearizing $\sqrt{x}$ around $x=4$.
* **Step 1 (Old Value):** $f(4) = \sqrt{4} = 2$.
* **Step 2 (Slope):** Derivative of $\sqrt{x}$ is $\frac{1}{2\sqrt{x}}$. At $x=4$, slope $= \frac{1}{2(2)} = 0.25$.
* **Step 3 (Step):** We moved from $4$ down to $3.9$. Step $= -0.1$.
* **Step 4 (Math):** Estimate $= 2 + (0.25 * -0.1) = 2 - 0.025 = 1.975$.
* **Answer:** $1.975$

### Question 6: Perpendicular Vectors
**Q:** Which of the following pairs of vectors are perpendicular to each other?
* **Exam Hack:** Vectors are perpendicular if their Dot Product equals **0**. Just multiply straight across and add.
* $[2, 3, 5]$ and $[-2, 3, -1] \rightarrow (2*-2) + (3*3) + (5*-1) = -4 + 9 - 5 = 0$. (Yes!)
* $[0, 1, 0]$ and $[0, 0, 1] \rightarrow 0 + 0 + 0 = 0$. (Yes!)
* $[1, 0, 0]$ and $[0, 1, 0] \rightarrow 0 + 0 + 0 = 0$. (Yes!)
* **Answers:** The three pairs listed above.

### Question 7: Multivariate Linear Approximation
**Q:** What is the linear approximation of $f(x,y) = x^3 + y^3$ around $(2, 2)$?
* **Step 1 (Old Value):** $f(2,2) = 2^3 + 2^3 = 8 + 8 = 16$.
* **Step 2 (Gradient/Slope):** Partial derivatives are $[3x^2, 3y^2]$. At $(2,2)$, this is $[12, 12]$.
* **Step 3 (Formula):** $L(x,y) = 16 + 12(x-2) + 12(y-2)$.
* **Step 4 (Algebra):** $16 + 12x - 24 + 12y - 24 = 12x + 12y - 32$.
* **Answer:** $12x + 12y - 32$

### Question 8: Calculating Gradients (2D)
**Q:** What is the gradient of $f(x,y) = x^3 y^2$ at $(1, 2)$?
* **Step 1 ($\partial/\partial x$):** Treat $y$ as a constant. Derivative is $3x^2 y^2$. Plug in $(1,2) \rightarrow 3(1^2)(2^2) = 12$.
* **Step 2 ($\partial/\partial y$):** Treat $x$ as a constant. Derivative is $2x^3 y$. Plug in $(1,2) \rightarrow 2(1^3)(2) = 4$.
* **Answer:** $[12, 4]$

### Question 9: Calculating Gradients (3D)
**Q:** The gradient of $f = x^3 + y^2 + z^3$ at $x=0, y=1, z=1$ is given by:
* **Step 1 ($\partial/\partial x$):** $3x^2 \rightarrow 3(0^2) = 0$.
* **Step 2 ($\partial/\partial y$):** $2y \rightarrow 2(1) = 2$.
* **Step 3 ($\partial/\partial z$):** $3z^2 \rightarrow 3(1^2) = 3$.
* **Answer:** $[0, 2, 3]$

### Question 10: Cauchy-Schwarz Inequality
**Q:** For two vectors $a$ and $b$, which of the following is true?
* **Exam Hack:** The Cauchy-Schwarz inequality just proves that the dot product is trapped between the negative and positive lengths of the vectors.
* $a^T b \le ||a|| * ||b||$ (True, max value)
* $a^T b \ge -||a|| * ||b||$ (True, min value)
* **Answer:** (i) and (ii)

### Question 11: Directional Derivative
**Q:** Directional derivative of $f(x,y,z) = x^3 + y^2 + z^3$ at $(1, 1, 1)$ along $v = [1, -2, 1]$.
* **Formula:** $D_v f = \text{Gradient} \cdot \text{Unit Vector}$
* **Step 1 (Gradient):** $[3x^2, 2y, 3z^2]$. At $(1,1,1) = [3, 2, 3]$.
* **Step 2 (Unit Vector):** Find the length of $v$: $\sqrt{1^2 + (-2)^2 + 1^2} = \sqrt{6}$. Divide $v$ by this: $[1/\sqrt{6}, -2/\sqrt{6}, 1/\sqrt{6}]$.
* **Step 3 (Dot Product):** $(3 * 1/\sqrt{6}) + (2 * -2/\sqrt{6}) + (3 * 1/\sqrt{6}) = (3 - 4 + 3) / \sqrt{6} = 2 / 2.449 \approx 0.816$.
* **Answer:** $0.816$

### Question 12: Direction of Steepest Ascent
**Q:** The direction of steepest ascent for $2x + y^3 + 4z$ at $(1, 0, 1)$ is:
* **Exam Hack:** Steepest ascent is ALWAYS just the normalized Gradient vector.
* **Step 1 (Gradient):** $[2, 3y^2, 4]$. At $(1,0,1) = [2, 0, 4]$.
* **Step 2 (Normalize):** Length is $\sqrt{2^2 + 0 + 4^2} = \sqrt{20}$. Divide the gradient by this length.
* **Answer:** $[\frac{2}{\sqrt{20}}, 0, \frac{4}{\sqrt{20}}]$

### Question 13: Directional Derivative (Another one)
**Q:** Directional derivative of $f(x,y,z) = x + y + z$ at $(-1, 1, 0)$ along $v=[1, -1, 1]$.
* **Step 1 (Gradient):** $[1, 1, 1]$. (It's a linear function, so gradient is constant).
* **Step 2 (Unit Vector):** Length of $v = \sqrt{1^2 + (-1)^2 + 1^2} = \sqrt{3}$. Unit vector $= [1/\sqrt{3}, -1/\sqrt{3}, 1/\sqrt{3}]$.
* **Step 3 (Dot Product):** $[1, 1, 1] \cdot [1/\sqrt{3}, -1/\sqrt{3}, 1/\sqrt{3}] = (1 - 1 + 1) / \sqrt{3} = 1/\sqrt{3} \approx 0.577$.
* **Answer:** $0.577$ (Range accepted $0.548 - 0.605$)

### Question 14: Equation of a Line
**Q:** Which of the following is the equation of the line passing through $[7, 8, 6]$ in the direction of vector $[1, 2, 3]$?
* **Exam Hack:** The formula for a line is `Starting Point + alpha * Direction Vector`. 
* Just plug the numbers straight in!
* **Answer:** $[7, 8, 6] + \alpha [1, 2, 3]$
