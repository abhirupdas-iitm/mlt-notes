## WEEK 10 — SUPPORT VECTOR MACHINES (SVM), DUALITY & MAXIMUM MARGIN
### 1. REVISITING PERCEPTRON
#### Key Result
- Mistakes≤R²/γ²
#### Insight
- Performance depends on margin γ
---
### 2. CORE QUESTION
#### Motivation (Page 1)
- Larger margin → better generalization
#### Question
- Can we directly find classifier with maximum margin?
---
### 3. LINEAR SEPARABILITY
#### Assumption
- ∃ w such that:
  yᵢ(wᵀxᵢ)≥γ
---
### 4. SCALING ISSUE
#### Problem
- If w works → cw also works
#### Fix
- Normalize:
  yᵢ(wᵀxᵢ)≥1
---
### 5. MARGIN DEFINITION
#### Width of margin (Page 2)
- width(w)=2/||w||
#### Goal
- Maximize margin
---
### 6. OPTIMIZATION PROBLEM
#### Equivalent Form
- max 2/||w||
#### Convert to minimization:
- min(1/2)||w||²
#### Subject to:
- yᵢ(wᵀxᵢ)≥1
---
### 7. PRIMAL FORMULATION
#### Final Problem
- min(1/2)||w||²  
  s.t. yᵢ (wᵀxᵢ)≥1 ∀ i
---
### 8. GENERAL CONSTRAINED OPTIMIZATION
#### Form
- min f(w)  
  s.t. g(w) ≤ 0
---
### 9. LAGRANGIAN
#### Definition (Page 4)
- L(w, α) = f(w)+Σαᵢgᵢ(w)
#### αᵢ ≥ 0
---
### 10. SVM LAGRANGIAN
#### For SVM
- gᵢ(w) = 1−yᵢ(wᵀxᵢ)
#### L(w, α) =
- (1/2)||w||² + Σαᵢ(1−yᵢ wᵀxᵢ)
---
### 11. DUAL PROBLEM
#### Idea
- min over w → max over α
#### Result (Page 6)
- maxΣαᵢ−(1/2)ΣΣαᵢαⱼ yᵢyⱼ (xᵢᵀxⱼ)
#### Subject to:
- αᵢ≥0
---
### 12. REPRESENTATION OF w
#### Key Result (Page 6)
- w*=Σαᵢyᵢxᵢ
#### Insight
- w is linear combination of data points
---
### 13. IMPORTANT OBSERVATION
#### From Dual (Page 7)
- Depends only on:
  xᵢᵀxⱼ
#### Result
- Can use kernels
---
### 14. COMPLEMENTARY SLACKNESS
#### Condition (Page 8)
- αᵢ [1−yᵢ(wᵀxᵢ)] = 0
---
### 15. INTERPRETATION
#### If αᵢ > 0
- yᵢ(wᵀxᵢ) = 1
#### Meaning
- Point lies on margin
---
### 16. SUPPORT VECTORS
#### Definition (Page 9)
- Points with αᵢ>0
#### Insight
- Only these points define w
#### Key Idea
- Sparse solution
---
### 17. PREDICTION FUNCTION
#### Form
- f(x) = wᵀx
#### Substitute w:
- f(x) = Σαᵢyᵢ(xᵢᵀx)
#### Kernel version:
- f(x) = ΣαᵢyᵢK(xᵢ, x)
---
### 18. GEOMETRIC INTERPRETATION
#### Insight (Page 9)
- Only boundary points matter
- Interior points irrelevant
---
### 19. LIMITATION — OUTLIERS
#### Problem (Page 10)
- Hard constraint:
  yᵢ(wᵀxᵢ)≥1
- Not robust to noise
---
### 20. SOFT MARGIN SVM
#### Idea
- Allow violations
#### Introduce slack variables:
- ξᵢ≥0
---
### 21. SOFT MARGIN OBJECTIVE
#### Formulation
- min(1/2)||w||² + CΣξᵢ
#### Subject to:
- yᵢ(wᵀxᵢ)≥(1−ξᵢ)
---
### 22. ROLE OF C
#### Interpretation
- C = penalty for misclassification
#### Behavior
- Large C → strict classification
- Small C → more tolerance
---
### 23. FINAL INSIGHTS
#### Core Ideas
- Max margin improves generalization
- SVM = convex optimization problem
- Dual allows kernel trick
- Only support vectors matter
- Soft margin handles noise
---
### MEMORY LINES
#### Quick Recall
- min (1/2)||w||²
- yᵢ(wᵀxᵢ) ≥ 1
- w = Σ αᵢ yᵢ xᵢ
- αᵢ > 0 → support vector
- f(x) = Σ αᵢ yᵢ K(xᵢ,x)
- Soft margin: + C Σ ξᵢ
---
