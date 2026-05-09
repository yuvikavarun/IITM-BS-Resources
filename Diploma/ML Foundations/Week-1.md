# Core Concepts:

1. **Supervised vs. Unsupervised:** 
   * Supervised = Has labels/answers (Input + Output). *Examples: Predicting price, Spam detection.*
   * Unsupervised = No labels (Input only). *Examples: Grouping customers, clustering Wikipedia articles.*
2. **Regression vs. Classification:**
   * Regression = Predicting a continuous number (Price, Temp). Loss function uses Squares $(f(x)-y)^2$ or Absolute difference $|f(x)-y|$.
   * Classification = Predicting a category (Spam/Not Spam). Loss function uses the Indicator Function $\mathbf{1}(f(x) \neq y)$ to count mistakes.
3. **The Data Split:**
   * **Training Set:** Used to fit the model (learn the math).
   * **Validation Set:** Used for model selection (choosing linear vs quadratic).
   * **Test Set:** Used to compute generalization error (final score).
4. **The Loss Functions:**
   * $-\log(P(X))$ = Density Estimation (Probabilities).
   * $\sum ||g(f(X)) - X||^2$ = Dimensionality Reduction (Encode $\rightarrow$ Decode $\rightarrow$ Compare).

---

# Graded Assignment 1

### Question 1: Dimensions
**Q:** $[2, 4, -5]$ belongs to which of the following?
**Solution:** The number of items inside the bracket tells you the dimension ($d$). There are 3 numbers.
**Answer:** $\mathbb{R}^3$

### Question 2: Loss Functions
**Q:** Which of the following may *not* be an appropriate choice of loss function for regression?
**Solution:** Regression loss measures *distance* (using squares or absolute values). Classification loss *counts mistakes*. 
**Exam Hack:** If you see the bold **1** (indicator function) or a $\neq$ sign, it belongs to Classification, NEVER Regression.
**Answer:** $\frac{1}{n} \sum_{i=1}^n \mathbf{1}(f(x_i) \neq y_i)$

### Question 3: Identifying the Task
**Q:** Identify which of the following requires use of classification technique.
**Solution:** Can the answer be a decimal like 4.5? Rainfall (Yes). Price (Yes). Covid cases (Yes). Spam? (No, it's a category).
**Answer:** Predicting whether an email is spam or not.

### Question 4: The Indicator Function
**Q:** Mark all incorrect statements regarding the indicator function $\mathbf{1}()$.
**Solution:** The indicator function outputs `1` if the statement inside is TRUE, and `0` if FALSE. 
* statement: $(355 \% 2 = 0)$. The remainder of $355/2$ is $1$, not $0$. So the statement is FALSE. The output should be `0`.
**Answer:** $\mathbf{1}(355 \% 2 = 0) = 1$ is an incorrect statement.

### Question 5: Supervised vs Unsupervised
**Q:** Which of the following is false regarding supervised and unsupervised machine learning?
**Answer:** "In unsupervised learning model, the data contains both input and output variables while in supervised learning model, the data contains only input data." (This statement has them completely backwards).

### Question 6: Output of Regression
**Q:** The output of regression model is:
**Solution:** Regression outputs continuous numbers. Unless restricted by the specific math problem, it can span any range on the number line.
**Answer:** is continuous with any range.

### Question 7: Identifying Supervised Tasks
**Q:** Which of the following is/are supervised learning task(s)?
**Solution:** Look for historical examples where the "answer" is known. 
**Answer:** Predicting whether a loan client may default (Classification). Estimating the revenue of a company (Regression).

### Question 8: Continuous Targets
**Q:** Which of the following is used for predicting a continuous target variable?
**Answer:** Regression

### Question 9: The Data Sets
**Q:** The is _____ used to fit the model; the _____ is used for model selection; the _____ is used for computing the generalization error.
**Answer:** Training set; Validation set; Test set

### Question 10: Matching Loss Functions
**Q:** Match the loss formulas to the technique.
**Exam Hack:** 
* Look for `log` and `P()` $\rightarrow$ Density Estimation.
* Look for $g(f(x))$ (Encode/Decode) $\rightarrow$ Dimensionality Reduction.
* Look for $(f(X) - Y)^2$ $\rightarrow$ Regression.
* Look for $\mathbf{1}(f(x) \neq y)$ $\rightarrow$ Classification.
**Answer:** Density Estimation, Dimensionality Reduction, Regression, Classification

---

### Questions 11 & 12: Dimensionality Reduction Math
**Given:** 4 data points. Loss function is average squared distance between original $x$ and decoded output $g(f(x))$.
$x^1 = [1, 0.5]$, $x^2 = [2, 2.3]$, $x^3 = [3, 3.1]$, $x^4 = [4, 3.9]$

**Q11 (Pair 1):** $f(x) = (x_1 - x_2)$, $g(u) = [u/2, u/2]$
* **Step 1 (Encode $x^1$):** $u = 1 - 0.5 = 0.5$
* **Step 2 (Decode):** $g(0.5) = [0.25, 0.25]$
* **Step 3 (Squared Error):** $(0.25 - 1)^2 + (0.25 - 0.5)^2 = (-0.75)^2 + (-0.25)^2 = 0.5625 + 0.0625 = 0.625$
* *Repeat for all 4 points, add them up, divide by 4.* (Result: $15.225$)

**Q12 (Pair 2):** $f(x) = (x_1 + x_2)/2$, $g(u) = [u/2, u/2]$
* **Step 1 (Encode $x^1$):** $u = (1 + 0.5) / 2 = 0.75$
* **Step 2 (Decode):** $g(0.75) = [0.375, 0.375]$
* **Step 3 (Squared Error):** $(0.375 - 1)^2 + (0.375 - 0.5)^2 = (-0.625)^2 + (-0.125)^2 = 0.3906 + 0.0156 = 0.40625$
* *Repeat for all 4 points, add them up, divide by 4.* 
* **Exam Hack:** If you are running out of time, skip manual calculations like this and do the conceptual questions first!

---

### Questions 13, 14 & 15: Regression Math
**Q13:** Given data points, which parameters $(a,b)$ for $f(x) = ax + b$ are best?
* **Exam Hack:** Don't calculate the exact loss for all 4 options! Just plug the $(a,b)$ values into a data point and see which prediction is closest.
* Try $(1,1) \rightarrow f(x) = 1x + 1$. 
* Test data point $x=1$. Formula gives $f(1) = 2$. The actual target $y$ is $1.9566$. That's incredibly close! The other options will be way off. 
**Answer:** $(1, 1)$

**Q14 & 15:** Calculate the exact average squared error for $g = 3x_1 + 1$ and $h = 2x_1 + 2$.
* Take $X=[2], y=5.8$. 
* Prediction for $g$: $3(2) + 1 = 7$.
* Squared error: $(7 - 5.8)^2 = 1.2^2 = 1.44$.
* *Repeat for all points, sum, and divide by $n=5$.*

---

### Questions 16 & 17: Classification Math (Misclassification Error)
**The Concept:** You are classifying points into $+1$ or $-1$. The "Sign" function outputs $+1$ if the number is $\ge 0$, and $-1$ if the number is $< 0$.
**Loss Formula:** (Number of mistakes) / (Total number of points). Total points $n=6$.

**Q16: Loss for $g(X) = sign(x_1 - x_2 - 2)$**
Let's test the points to find mistakes:
1. $X=[4, 2]$, True $y=+1$. Formula: $4 - 2 - 2 = 0 \rightarrow sign(0) = +1$. (Match)
2. $X=[8, 4]$, True $y=+1$. Formula: $8 - 4 - 2 = 2 \rightarrow sign(2) = +1$. (Match)
3. $X=[2, 6]$, True $y=-1$. Formula: $2 - 6 - 2 = -6 \rightarrow sign(-6) = -1$. (Match)
4. $X=[4, 10]$, True $y=-1$. Formula: $4 - 10 - 2 = -8 \rightarrow sign(-8) = -1$. (Match)
5. $X=[10, 2]$, True $y=+1$. Formula: $10 - 2 - 2 = 6 \rightarrow sign(6) = +1$. (Match)
6. $X=[12, 8]$, True $y=-1$. Formula: $12 - 8 - 2 = 2 \rightarrow sign(2) = +1$. **(MISTAKE!)**
* You made 1 mistake out of 6 points. Loss = $1/6 \approx 0.166$. 

**Q17: Loss for $h(X) = sign(x_1 + x_2 - 10)$**
1. $X=[4, 2]$, True $y=+1$. Formula: $4 + 2 - 10 = -4 \rightarrow sign(-4) = -1$. **(MISTAKE!)**
2. $X=[8, 4]$, True $y=+1$. Formula: $8 + 4 - 10 = 2 \rightarrow sign(2) = +1$. (Match)
3. $X=[2, 6]$, True $y=-1$. Formula: $2 + 6 - 10 = -2 \rightarrow sign(-2) = -1$. (Match)
4. $X=[4, 10]$, True $y=-1$. Formula: $4 + 10 - 10 = 4 \rightarrow sign(4) = +1$. **(MISTAKE!)**
5. $X=[10, 2]$, True $y=+1$. Formula: $10 + 2 - 10 = 2 \rightarrow sign(2) = +1$. (Match)
6. $X=[12, 8]$, True $y=-1$. Formula: $12 + 8 - 10 = 10 \rightarrow sign(10) = +1$. **(MISTAKE!)**
* You made 3 mistakes out of 6 points. Loss = $3/6 = 0.5$.
```eof
