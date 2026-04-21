## WEEK 6 — REGULARIZATION, RIDGE, LASSO & BAYESIAN INTERPRETATION
### 1. PROBLEM WITH LINEAR REGRESSION
#### Recall
- ŵ<sub>ML</sub> = (X<sup>T</sup>X)<sup>−1</sup>X<sup>T</sup>y
#### Issue
- Can overfit data
- Sensitive to noise
#### Need
- Control model complexity
---
### 2. REGULARIZATION IDEA
#### Modify Objective
- Add penalty term:
  min Σ (w<sup>T</sup>xᵢ−yᵢ)² + λ||w||²
#### λ (lambda)
- Controls strength of regularization
---
### 3. RIDGE REGRESSION (L2)
#### Objective
- min Σ (w<sup>T</sup>xᵢ−yᵢ)² + λ||w||²
#### Equivalent Form (Page 1)
- min Σ (w<sup>T</sup>xᵢ−yᵢ)²  
  subject to ||w||²≤θ
#### Insight
- Penalty ↔ constraint equivalence
---
### 4. GEOMETRIC INTERPRETATION
#### From Diagram (Page 2)
- Error → elliptical contours
- Constraint → circular region
#### Solution
- Point where ellipse touches constraint region
#### Insight
- Regularization shrinks weights toward zero
---
### 5. EFFECT OF RIDGE
#### Behavior
- Reduces magnitude of weights
- Does NOT make them exactly zero
#### Result
- More stable solution
---
### 6. L1 REGULARIZATION (LASSO)
#### Objective
- min Σ(w<sup>T</sup>xᵢ − yᵢ)²+λ||w||₁
#### L1 Norm
- ||w||₁=Σ|wᵢ|
---
### 7. GEOMETRIC DIFFERENCE
#### L2 (Ridge)
- Constraint: circle
#### L1 (LASSO)
- Constraint: diamond shape
#### Result (Page 3)
- Corners → weights become exactly zero
---
### 8. KEY PROPERTY OF LASSO
#### Feature Selection
- Produces sparse solution
- Some wᵢ = 0
#### Insight
- Automatically selects important features
---
### 9. OPTIMIZATION ISSUE
#### Ridge
- Closed form solution exists
#### LASSO
- No closed form
#### Solution
- Sub-gradient methods
---
### 10. SUB-GRADIENT
#### Definition (Page 4)
- g is subgradient if:
  f(z)≥f(x)+g<sup>T</sup>(z − x)
#### Use
- For non-differentiable functions (like |x|)
---
### 11. WHY REGULARIZATION HELPS
#### Problem
- High variance in estimates
#### Insight
- Adding bias reduces variance
#### Trade-off
- Bias vs Variance
---
### 12. ANALYSIS OF MLE
#### Result (Page 1)
- E[||ŵ<sub>ML</sub>−w||²] = σ² trace((X<sup>T</sup>X)<sup>−1</sup>)
#### Insight
- Large variance when X<sup>T</sup>X is ill-conditioned
---
### 13. RIDGE SOLUTION
#### Modified Estimator
- ŵ = (X<sup>T</sup>X+λI)<sup>−1</sup>X<sup>T</sup>y
#### Effect
- Improves conditioning of matrix
---
### 14. CROSS VALIDATION
#### Problem
- How to choose λ?
#### Method (Page 2)
- Split data:
  - Train set
  - Validation set
#### K-Fold CV
- Divide into K folds
- Train on K−1, validate on remaining
#### Goal
- Choose λ minimizing validation error
---
### 15. BAYESIAN INTERPRETATION
#### Likelihood
- y = w<sup>T</sup>x + ε, ε ~ N(0, σ²)
#### Prior on w
- w ~ N(0, γ²I)
---
### 16. POSTERIOR
#### Expression
- P(w|data) ∝ likelihood × prior
#### MAP Estimation
- ŵ<sub>MAP</sub> = argmax P(w|data)
---
### 17. MAP OBJECTIVE
#### Equivalent Form (Page 3)
- min Σ (w<sup>T</sup>xᵢ−yᵢ)² + (σ²/γ²) ||w||²
#### Insight
- Same as ridge regression
---
### 18. FINAL RESULT
#### Key Equivalence
- Ridge regression ⇔ MAP estimation with Gaussian prior
---
### 19. FINAL INSIGHTS
#### Core Ideas
- Regularization prevents overfitting
- Ridge shrinks weights
- LASSO creates sparsity
- λ controls bias-variance tradeoff
- Bayesian view explains regularization
---
### MEMORY LINES
#### Quick Recall
- Ridge: + λ||w||²
- LASSO: + λ||w||₁
- Ridge solution: (XᵀX + λI)⁻¹Xᵀy
- LASSO → sparse
- MAP ⇔ Ridge
- λ → bias vs variance
---
