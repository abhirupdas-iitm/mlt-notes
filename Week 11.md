## WEEK 11 — ENSEMBLE METHODS: BAGGING, RANDOM FORESTS & BOOSTING
### 1. RECAP — MODEL TYPES
#### Generative Models
- Naive Bayes
- Gaussian Models
#### Discriminative Models
- K-NN
- Decision Trees
- Logistic Regression
- Perceptron
- SVM
---
### 2. MOTIVATION — META LEARNING
#### Goal (Page 1)
- Combine multiple models
#### Idea
- Weak learners → Strong learner
#### Weak Learner
- Slightly better than random
---
### 3. BIAS-VARIANCE TRADEOFF
#### Error Decomposition
- Error = Bias + Variance
#### Overfitting (Page 1)
- High variance
- Fits noise
#### Underfitting
- High bias
- Misses structure
---
### 4. BAGGING (BOOTSTRAP AGGREGATION)
#### Key Idea
- Train multiple models on different datasets
---
### 5. BOOTSTRAPPING
#### Definition (Page 2)
- Sampling with replacement
#### Insight
- Each dataset Dᵢ slightly different
---
### 6. BAGGING ALGORITHM
#### Steps
1. Create datasets D₁, D₂, ..., Dₘ using bootstrap
2. Train model h₁, h₂, ..., hₘ
3. Aggregate predictions:
   h(x) = sign((1/m)Σhᵢ(x))
---
### 7. WHY BAGGING WORKS
#### Key Insight (Page 2)
- Averaging reduces variance
#### Property
- E[θ̂] = θ (unbiased)
- Variance ↓ after averaging
---
### 8. IMPORTANT RESULT
#### Probability (Page 3)
- Probability a sample is included:
  ≈ 1−1/e ≈ 0.63
#### Meaning
- Each bootstrap dataset uses ~63% unique data
---
### 9. RANDOM FORESTS
#### Idea (Page 3)
- Bagging + decision trees
#### Modification
- Feature bagging:
  - Use subset of features at each split
#### Benefit
- Reduces correlation between trees
---
### 10. SUMMARY — BAGGING
#### Key Points
- Parallelizable
- Reduces variance
- Works well for high-variance models (like trees)
---
### 11. BOOSTING — CORE IDEA
#### Contrast with Bagging
- Bagging: independent models
- Boosting: sequential models
#### Goal
- Focus on hard examples
---
### 12. ADABOOST
#### Setup (Page 4)
- Weak learners: decision stumps
#### Input
- Dataset S = {(xᵢ, yᵢ)}
---
### 13. INITIALIZATION
#### Weights
- D₁(i)=1/n
---
### 14. ITERATIVE PROCESS
For t = 1,...,T:
#### Step 1: Train Weak Learner
- hₜ trained using weights Dₜ
#### Step 2: Compute Error
- εₜ = weighted error of hₜ
#### Step 3: Compute Weight
- αₜ = ln((1−εₜ)/εₜ )
#### Step 4: Update Weights
- If misclassified:
  Dₜ₊₁(i) ∝ Dₜ(i) e^{αₜ}
- If correct:
  Dₜ₊₁(i) ∝ Dₜ(i) e^{−αₜ}
#### Step 5: Normalize
- Ensure ΣDₜ₊₁(i) = 1
---
### 15. FINAL MODEL
#### Prediction
- h(x) = sign(Σαₜhₜ(x))
---
### 16. KEY INTUITION
#### Insight (Page 4)
- Misclassified points → higher weight
- Model focuses on difficult points
---
### 17. PERFORMANCE GUARANTEE
#### Result (Page 5)
- Training error decreases exponentially
#### Condition
- Weak learner must be better than random
---
### 18. IMPORTANT PROPERTY
#### Sequential Nature
- Cannot parallelize easily
---
### 19. BAGGING VS BOOSTING
#### Bagging
- Parallel
- Reduces variance
#### Boosting
- Sequential
- Reduces bias + variance
---
### 20. FINAL INSIGHTS
#### Core Ideas
- Ensemble = combine models
- Bagging reduces variance
- Random Forest improves bagging
- Boosting focuses on hard samples
- AdaBoost builds strong classifier from weak ones
---
### MEMORY LINES
#### Quick Recall
- Bagging = bootstrap + average
- ~63% data per sample
- Random Forest = trees + feature bagging
- Boosting = sequential learning
- α = ln((1−ε)/ε)
- h(x) = sign(Σ αₜ hₜ(x))
---