## WEEK 5 — SUPERVISED LEARNING, LINEAR REGRESSION, SGD & KERNEL REGRESSION
### 1. SUPERVISED LEARNING
#### Input
- Dataset:
  {(x₁, y₁), (x₂, y₂), ..., (xₙ, yₙ)}
- xᵢ ∈ ℝᵈ (features)
- yᵢ ∈ ℝ or discrete labels
#### Types
- Binary classification: y ∈ {0,1}
- Multiclass classification: y ∈ {1,...,K}
- Regression: y ∈ ℝ
---
### 2. REGRESSION PROBLEM
#### Goal
- Learn function:
  f : ℝᵈ → ℝ
#### Error Function
- Squared error:
  Error(f) = Σ (f(xᵢ) − yᵢ)²
#### Problem
- Minimizing error → can overfit training data
#### Solution
- Restrict hypothesis space
---
### 3. LINEAR REGRESSION
#### Hypothesis Class
- f<sub>w</sub>(x) = w<sup>T</sup>x
#### Objective
- min<sub>w</sub> Σ (w<sup>T</sup>xᵢ − yᵢ)²
#### Matrix Form
- min ||Xw − y||²
---
### 4. CLOSED FORM SOLUTION
#### Normal Equation
- w* = (X<sup>T</sup>X)<sup>†</sup> X<sup>T</sup>y
#### Insight (Page 2)
- Requires matrix inverse
#### Problem
- Computationally expensive:
  O(d³)
---
### 5. GRADIENT DESCENT
#### Objective Function
- f(w) = ||Xw − y||²
#### Gradient
- ∇f(w) = 2(X<sup>T</sup>X w − X<sup>T</sup>y)
#### Update Rule
- w<sup>t+1</sup> = w<sup>t</sup> − η ∇f(w<sup>t</sup>)
---
### 6. COMPUTATIONAL ISSUE
#### Problem
- Computing X<sup>T</sup>X expensive when n is large
#### Need
- Scalable optimization method
---
### 7. STOCHASTIC GRADIENT DESCENT (SGD)
#### Idea (Page 2)
- Use subset (mini-batch) instead of full dataset
#### Algorithm
For t = 1,...,T:
- Sample batch B
- Compute gradient on B
- Update:
  w ← w − η ∇f<sub>B</sub>(w)
#### Insight
- Faster per iteration
- Noisy but efficient
---
### 8. SGD OUTPUT
#### Final Estimate
- Average iterates:
  ŵ = (1/T) Σ w<sup>t</sup>
#### Property
- Converges with high probability
---
### 9. GEOMETRIC INTERPRETATION
#### Insight (Page 4)
- Xw* = projection of y onto column space of X
#### Meaning
- Best approximation of y using linear combinations of features
---
### 10. NON-LINEAR REGRESSION
#### Problem
- Linear model too restrictive
#### Idea
- Map features:
  x → φ(x)
- Then apply linear regression
---
### 11. REPRESENTATION IN DATA SPACE
#### Key Insight (Page 3)
- Solution lies in span of data:
  w* = X<sup>T</sup> α
#### Substitute into objective:
- Leads to dual formulation
---
### 12. KERNEL REGRESSION
#### Prediction
- f(x) = w<sup>T</sup>φ(x)
- = Σ αᵢ φ(xᵢ)<sup>T</sup> φ(x)
#### Using Kernel
- K(xᵢ, x) = φ(xᵢ)<sup>T</sup> φ(x)
#### Final Form
- f(x) = Σ αᵢ K(xᵢ, x)
---
### 13. KEY INTERPRETATION
#### Each term αᵢ
- Represents importance of training point
#### Kernel
- Measures similarity
---
### 14. PROBABILISTIC VIEW OF LINEAR REGRESSION
#### Model (Page 3)
- y = w<sup>T</sup>x + ε
#### Noise
- ε ~ N(0, σ²)
---
### 15. LIKELIHOOD
#### Expression (Page 4)
- L(w) = ∏ exp( −(w<sup>T</sup>xᵢ − yᵢ)² / 2σ² )
#### Log-Likelihood
- log L(w) ∝ − Σ (w<sup>T</sup>xᵢ − yᵢ)²
---
### 16. IMPORTANT RESULT
#### Equivalence
- Maximizing likelihood ⇔ minimizing squared error
#### Conclusion
- Linear regression = MLE under Gaussian noise
---
### 17. FINAL INSIGHTS
#### Core Ideas
- Supervised learning uses labeled data
- Linear regression = least squares
- Gradient descent for optimization
- SGD for scalability
- Kernel trick enables non-linearity
- Probabilistic view connects to MLE
---
### MEMORY LINES
#### Quick Recall
- f(x) = wᵀx
- w* = (XᵀX)⁻¹Xᵀy
- GD: w ← w − η∇f
- SGD: sample + update
- w = Xᵀα
- f(x) = Σ αᵢ K(xᵢ, x)
- MLE ⇔ least squares
---
