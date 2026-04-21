# Portfolio Risk Surface  
### A Quantitative Analysis of Portfolio Risk as a Function of Asset Allocation

---

## 🧠 Overview

This project studies how portfolio risk evolves as a function of asset allocation.  
We construct and visualize the **portfolio risk surface**, highlighting the nonlinear effects of diversification and correlation.

The goal is to move beyond simple intuition and provide a **continuous, mathematical view of risk across the allocation space**.

---

## 🎯 Objectives

- Model portfolio risk using covariance structure  
- Explore how weights influence total risk  
- Visualize risk as a continuous surface  
- Understand diversification and concentration effects  

---

## ⚙️ Mathematical Framework

### 1. Portfolio Weights

Let:

- \( w = (w_1, w_2, ..., w_n) \) be the portfolio weights  
- Constraint:  
  \[
  \sum_{i=1}^{n} w_i = 1
  \]

---

### 2. Covariance Matrix

Let:

- \( \Sigma \in \mathbb{R}^{n \times n} \) be the covariance matrix  

\[
\Sigma =
\begin{bmatrix}
\sigma_1^2 & \rho_{12}\sigma_1\sigma_2 & \dots \\
\rho_{21}\sigma_2\sigma_1 & \sigma_2^2 & \dots \\
\vdots & \vdots & \ddots
\end{bmatrix}
\]

Where:
- \( \sigma_i \) = volatility of asset \( i \)  
- \( \rho_{ij} \) = correlation between assets \( i \) and \( j \)

---

### 3. Portfolio Variance

The portfolio variance is given by:

\[
\text{Var}(w) = w^T \Sigma w
\]

This expands to:

\[
\text{Var}(w) = \sum_{i=1}^{n} w_i^2 \sigma_i^2 + \sum_{i \neq j} w_i w_j \sigma_i \sigma_j \rho_{ij}
\]

---

### 4. Portfolio Volatility

\[
\sigma_p = \sqrt{w^T \Sigma w}
\]

This is the primary risk metric used in the project.

---

### 5. Two-Asset Case (Intuition)

For two assets:

\[
\sigma_p^2 =
w_1^2 \sigma_1^2 +
w_2^2 \sigma_2^2 +
2 w_1 w_2 \sigma_1 \sigma_2 \rho
\]

This clearly shows:

- Quadratic dependence on weights  
- Linear dependence on correlation  
- Nonlinear diversification effects  

---

## 📊 Risk Surface Construction

We discretize the weight space:

\[
w_1, w_2 \in [0,1], \quad w_3 = 1 - w_1 - w_2
\]

subject to:

\[
w_i \geq 0
\]

For each valid weight vector:

1. Compute covariance matrix  
2. Compute portfolio variance  
3. Store result  

This produces a mapping:

\[
(w_1, w_2) \rightarrow \sigma_p
\]

---

## 📈 Visualization

The risk surface is visualized using:

- Heatmaps  
- Contour plots  
- 3D surface plots  

These reveal:

- Risk valleys (diversification benefit)  
- Risk peaks (concentration)  
- Curvature driven by correlation  

---

## 🔍 Key Insights

### 1. Diversification is Nonlinear
Risk does not decrease linearly with diversification.

### 2. Correlation is Critical
- Low correlation → deep risk valleys  
- High correlation → flat or elevated surfaces  

### 3. Concentration Risk
Portfolios heavily weighted toward a single asset exhibit significantly higher risk.

### 4. Geometry of Risk
The risk surface is a **quadratic form**, resulting in smooth curvature across the allocation space.

---

## ⚠️ Assumptions

- Static covariance matrix  
- No transaction costs  
- No time dynamics  
- Perfect knowledge of parameters  

---

## 🚀 How to Run

```bash
pip install -r requirements.txt
jupyter notebook
