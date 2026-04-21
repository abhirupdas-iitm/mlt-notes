## WEEK 7 — CLASSIFICATION, K-NN, DECISION TREES & MODEL TYPES
### 1. SUPERVISED LEARNING — CLASSIFICATION
#### Input
- Dataset:
  {(x₁, y₁), ..., (xₙ, yₙ)}
- xᵢ ∈ ℝᵈ
- yᵢ ∈ {0,1} (binary classification)
#### Goal
- Learn function:
  h : ℝᵈ → {0,1}
---
### 2. LOSS FUNCTION (0–1 LOSS)
#### Definition
- Loss(h) = (1/n)Σ1(h(xᵢ)≠yᵢ)
#### Indicator Function
- 1(z)=1 if z true, else 0
#### Objective
- minΣ1(h(xᵢ) ≠ yᵢ)
#### Issue
- NP-hard optimization problem
---
### 3. LINEAR CLASSIFIER
#### Hypothesis
- h<sub>w</sub>(x) = sign(w<sup>T</sup>x)
#### Insight (Page 1)
- Decision boundary: hyperplane
---
### 4. CAN WE USE LINEAR REGRESSION?
#### Idea
- Fit regression model
- Threshold output
#### Problem
- Sensitive to magnitude, not just sign
#### Conclusion (Page 1)
- Regression is not ideal for classification
---
### 5. SIMPLE CLASSIFICATION — NEAREST NEIGHBOUR
#### Algorithm (Page 2)
- Given x<sub>test</sub>:
  - Find closest training point x'
  - Predict y<sub>test</sub> = y'
#### Issue
- Sensitive to outliers
---
### 6. K-NEAREST NEIGHBOURS (K-NN)
#### Algorithm
- Find k closest points:
  {x₁*, x₂*, ..., xₖ*}
- Predict:
  y<sub>test</sub> = majority(y₁*, ..., yₖ*)
---
### 7. EFFECT OF K
#### Small K (e.g., K=1)
- Complex decision boundary
- Sensitive to noise
#### Large K (e.g., K=n)
- Smooth boundary
- May underfit
#### Insight (Page 3)
- Trade-off: bias vs variance
---
### 8. CHOOSING K
#### Method
- Treat K as hyperparameter
- Use cross-validation
---
### 9. ISSUES WITH K-NN
#### Problems
- Choosing distance metric
- Computationally expensive at prediction
- No explicit model learned
---
### 10. DECISION TREES
#### Idea (Page 4)
- Recursively split data using questions
#### Structure
- Internal nodes → questions
- Leaves → predictions
---
### 11. QUESTION FORM
#### Format
- (feature, threshold)
#### Example
- f₁ ≤ θ ?
---
### 12. DATA SPLIT
#### Partition
- D → D<sub>yes</sub>, D<sub>no</sub>
---
### 13. NEED FOR SPLIT CRITERION
#### Goal
- Measure "goodness" of a split
#### Need
- Impurity measure
---
### 14. ENTROPY
#### Definition (Page 5)
- For binary labels:
  H(p) = − [p log p + (1−p) log(1−p)]
#### Interpretation
- Measures uncertainty
#### Properties
- Max at p = 0.5
- Min at p = 0 or 1
---
### 15. INFORMATION GAIN
#### Definition
- IG = H(D)−[γ H(D<sub>yes</sub>) + (1−γ) H(D<sub>no</sub>)]
Where:
- γ = |D<sub>yes</sub>|/|D|
#### Goal
- Maximize information gain
---
### 16. DECISION TREE ALGORITHM
#### Steps (Page 6)
1. Choose best split (max IG)
2. Partition data
3. Repeat recursively
---
### 17. STOPPING CRITERIA
#### Conditions
- Node is pure
- Depth limit reached
- Few samples left
#### Note
- Tree depth = hyperparameter
---
### 18. ALTERNATIVE METRIC
#### Gini Index
- Another impurity measure
---
### 19. DECISION BOUNDARY
#### Insight (Page 7)
- Axis-aligned splits
- Produces rectangular regions
---
### 20. TYPES OF MODELING
#### Data View (Page 8)
- Data drawn from distribution D
---
### 21. GENERATIVE MODEL
#### Model
- Learn joint distribution:

  P(x, y)
#### Use
- Can generate data
---
### 22. DISCRIMINATIVE MODEL
#### Model
- Learn conditional:
  P(y | x)
#### Examples
- K-NN
- Decision Trees
---
### 23. KEY DIFFERENCE
#### Generative
- Models how data is generated
#### Discriminative
- Focuses on decision boundary
---
### 24. FINAL INSIGHTS
#### Core Ideas
- Classification uses discrete outputs
- 0–1 loss is hard to optimize
- K-NN is simple but expensive
- Decision trees split using information gain
- Entropy measures uncertainty
- Models: generative vs discriminative
---
### MEMORY LINES
#### Quick Recall
- Loss = Σ 1(h(x) ≠ y)
- sign(wᵀx)
- K-NN → majority vote
- H(p) = −p log p − (1−p) log(1−p)
- IG = H(parent) − weighted children
- Tree = recursive splits
- Generative: P(x,y)
- Discriminative: P(y|x)
---
