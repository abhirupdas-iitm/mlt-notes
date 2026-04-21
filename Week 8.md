## WEEK 8 — NAIVE BAYES, GENERATIVE MODELS & GAUSSIAN CLASSIFICATION
### 1. GENERATIVE MODELING RECAP
#### Idea
- Model joint distribution:
  P(x, y)
#### Goal
- Use Bayes rule to compute:
  P(y|x)
#### Insight
- Learn how data is generated
---
### 2. SPAM CLASSIFICATION EXAMPLE
#### Representation
- x ∈ {0,1}<sup>d</sup>
- Each feature = presence/absence of word
#### Model
- P(x, y) = P(y)P(x | y)
---
### 3. PROBLEM — TOO MANY PARAMETERS
#### Without Assumption
- Need:
  P(x|y) → 2<sup>d</sup> parameters
#### Total parameters
- ≈ 2<sup>d+1</sup>
#### Issue
- Infeasible for large d
---
### 4. NAIVE BAYES ASSUMPTION
#### Key Idea
- Features are conditionally independent given label:
  P(x|y) = ∏P(x<sub>j</sub>|y)
#### Result
- Parameters reduce to:
  2d+1
#### Insight
- Huge simplification
---
### 5. MODEL PARAMETERS
#### Components
- p = P(y = 1)
- p<sub>j</sub><sup>(1)</sup>=P(x<sub>j</sub> = 1|y = 1)
- p<sub>j</sub><sup>(0)</sup>=P(x<sub>j</sub> = 1|y = 0)
---
### 6. MAXIMUM LIKELIHOOD ESTIMATION
#### Class Prior
- p̂ = (1/n)Σyᵢ
#### Conditional Probabilities
- p̂<sub>j</sub><sup>(y)</sup> =  
  (number of samples with x<sub>j</sub>=1 and y)  
  ---------------------------------------------  
  (number of samples with label y)
#### Interpretation (Page 1)
- Fraction of class-y samples containing feature j
---
### 7. PREDICTION USING BAYES RULE
#### Decision Rule
- Predict y = 1 if:
  P(y=1|x) > P(y=0|x)
#### Using Bayes:
- P(y|x) ∝ P(x|y)P(y)
---
### 8. NAIVE BAYES CLASSIFIER
#### Compute
- P(x|y=1) = ∏ (p<sub>j</sub><sup>(1)</sup>)<sup>x<sub>j</sub></sup> (1−p<sub>j</sub><sup>(1)</sup>)<sup>(1−x<sub>j</sub>)</sup>
- P(x|y=0) similarly
#### Final Decision
- Compare:
  P(x|y=1)p  vs  P(x|y=0)(1−p)
---
### 9. ZERO PROBABILITY PROBLEM
#### Issue (Page 3)
- If any p̂<sub>j</sub><sup>(y)</sup> = 0
- Entire product becomes zero
---
### 10. LAPLACE SMOOTHING
#### Fix
- Add pseudo counts
#### Idea
- Avoid zero probabilities
---
### 11. LOG TRANSFORMATION
#### Problem
- Products of many probabilities → numerical underflow
#### Solution
- Take log:
  log P(y=1|x) / P(y=0|x)
---
### 12. LINEAR DECISION FUNCTION
#### Result (Page 4)
- Decision rule becomes:
  w<sup>T</sup>x + b ≥ 0
Where:
- w<sub>j</sub> = log( p<sub>j</sub><sup>(1)</sup>(1−p<sub>j</sub><sup>(0)</sup) / (p<sub>j</sub><sup>(0)</sup>(1−p<sub>j</sub><sup>(1)</sup)) )

#### Conclusion
- Naive Bayes → **linear classifier** :contentReference[oaicite:3]{index=3}

---

### 13. GAUSSIAN GENERATIVE MODEL
#### Setup (Page 5)
- x | y=1 ~ N(μ₁, Σ)
- x | y=0 ~ N(μ₀, Σ)

#### Assumption
- Same covariance Σ

---

### 14. PARAMETER ESTIMATION
#### Mean
- μ̂₁ = average of class 1 points
- μ̂₀ = average of class 0 points

#### Covariance
- Σ̂ = (1/n) Σ (xᵢ − μ̂<sub>yᵢ</sub>)(xᵢ − μ̂<sub>yᵢ</sub>)<sup>T</sup>
---
### 15. PREDICTION
#### Using Bayes Rule
- Compare:
  P(x | y=1)p  vs  P(x | y=0)(1−p)
---
### 16. LINEAR DECISION BOUNDARY
#### When Σ is same (Page 6)
- Decision rule simplifies to:
  w<sup>T</sup>x+b≥0
#### Insight
- Linear separator
---
### 17. QUADRATIC BOUNDARY
#### When Σ differs (Page 7)
- Boundary becomes quadratic
#### Insight
- More flexible model
---
### 18. FINAL INSIGHTS
#### Core Ideas
- Generative models learn P(x,y)
- Naive Bayes assumes independence
- Massive reduction in parameters
- Log transforms → linear decision rule
- Gaussian models generalize NB
- Same Σ → linear, different Σ → quadratic
---
### MEMORY LINES
#### Quick Recall
- P(x,y) = P(y)P(x|y)
- Naive: P(x|y) = ∏ P(xⱼ|y)
- Params = 2d + 1
- Log → wᵀx + b
- Gaussian NB → linear
- Different Σ → quadratic boundary
---
