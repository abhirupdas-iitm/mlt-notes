## WEEK 9 — PERCEPTRON, LOGISTIC REGRESSION & CLASSIFICATION THEORY
### 1. CLASSIFICATION RECAP
#### Goal
- Learn:
  h : ℝᵈ→{−1, +1}
#### Two Approaches
- Generative → Naive Bayes, Gaussian
- Discriminative → Perceptron, Logistic Regression
---
### 2. SIMPLE LINEAR CLASSIFIER
#### Model
- h(x) = sign(w<sup>T</sup>x)
#### Interpretation
- Decision boundary = hyperplane
---
### 3. LIMITATION
#### Hard Decision
- P(y=1|x)=1 if w<sup>T</sup>x ≥ 0, else 0
#### Issue
- No notion of probability
---
### 4. PERCEPTRON ALGORITHM
#### Input
- {(x₁,y₁), ..., (xₙ,yₙ)}, yᵢ ∈ {−1, +1}
#### Initialization
- w⁰ = 0
---
#### Iteration
- Pick (xᵢ, yᵢ)
- If correctly classified:
  sign(w<sup>T</sup>xᵢ) = yᵢ → do nothing
- Else (mistake):
  w←w+yᵢ xᵢ
---
### 5. UPDATE INTERPRETATION
#### Insight (Page 2)
- Update pushes w in correct direction
#### Two Mistake Types
- False positive
- False negative
---
### 6. LINEAR SEPARABILITY ASSUMPTION
#### Definition
- Dataset is separable if:
  ∃ w such that:
  yᵢ(w<sup>T</sup>xᵢ)>0 ∀ i
---
### 7. MARGIN
#### Definition (Page 4)
- Dataset has margin γ if:
  yᵢ(w<sup>T</sup>xᵢ)≥γ
#### Meaning
- Distance from boundary
---
### 8. RADIUS ASSUMPTION
#### Definition
- ||xᵢ||≤R for all i
---
### 9. PERCEPTRON MISTAKE ANALYSIS
#### Key Observations
- Update occurs only on mistakes
- After k updates:
  w<sup>k</sup>=Σyᵢxᵢ
---
### 10. NORM BOUND
#### Result (Page 5)
- ||w<sup>k</sup>||²≤kR²
---
### 11. PROGRESS TOWARD TRUE w*
#### Result (Page 6)
- w<sup>k</sup>·w*≥kγ
---
### 12. COMBINING RESULTS
#### Using Cauchy-Schwarz
- (w<sup>k</sup> · w*)² ≤ ||w<sup>k</sup>||² ||w*||²
---
### 13. FINAL BOUND
#### Result (Page 6)
- k≤R²/γ²
#### Interpretation
- Number of mistakes is bounded
---
### 14. CONCLUSION
#### Key Result (Page 7)
- Perceptron converges if data is linearly separable
---
### 15. NEED FOR PROBABILISTIC MODEL
#### Problem
- Perceptron gives only hard classification
#### Need
- Estimate probabilities
---
### 16. LOGISTIC REGRESSION
#### Model
- Define:
  z=w<sup>T</sup>x
#### Probability
- P(y=1|x) = g(z)
---
### 17. SIGMOID FUNCTION
#### Definition (Page 2)
- g(z) = 1 / (1+e<sup>−z</sup>)
#### Properties
- g(0)=0.5
- g(z)→1 as z→∞
- g(z)→0 as z→−∞
---
### 18. LOGISTIC MODEL
#### Final Form
- P(y=1|x) = 1 / (1+e<sup>−w<sup>T</sup>x</sup>)
---
### 19. MAXIMUM LIKELIHOOD
#### Likelihood
- L(w) = ∏ g(w<sup>T</sup>xᵢ)<sup>yᵢ</sup> (1 − g(w<sup>T</sup>xᵢ))<sup>(1−yᵢ)</sup>
---
### 20. LOG-LIKELIHOOD
#### Expression (Page 2)
- log L(w) = Σ [yᵢ log g(w<sup>T</sup>xᵢ) + (1−yᵢ) log(1 − g(w<sup>T</sup>xᵢ))]
---
### 21. OPTIMIZATION
#### Goal
- Maximize log-likelihood
#### Issue
- No closed-form solution
#### Solution
- Gradient descent
---
### 22. GRADIENT
#### Result (Page 3)
- ∇ = Σxᵢ(yᵢ−g(w<sup>T</sup>xᵢ))
---
### 23. UPDATE RULE
#### Gradient Ascent
- w ← w+ηΣxᵢ(yᵢ−g(w<sup>T</sup>xᵢ))
---
### 24. INTERPRETATION
#### Insight
- If prediction too small → increase weight
- If too large → decrease weight
---
### 25. REGULARIZATION
#### Objective
- Add penalty:
  + (λ/2) ||w||²
---
### 26. KERNEL VERSION
#### Insight (Page 3)
- w=Σαᵢxᵢ
#### Result
- Kernel logistic regression
---
### 27. FINAL INSIGHTS
#### Core Ideas
- Perceptron = mistake-driven learning
- Converges with margin assumption
- Logistic regression = probabilistic model
- Uses sigmoid link function
- Optimized via gradient methods
---
### MEMORY LINES
#### Quick Recall
- Perceptron: w←w+yx
- Mistakes ≤ R²/γ²
- g(z) = 1/(1+e⁻ᶻ)
- ∇ = Σ xᵢ(yᵢ − g(wᵀxᵢ))
- No closed form → GD
- Logistic = probabilistic linear model
---
