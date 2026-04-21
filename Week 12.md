## WEEK 12 — LOSS FUNCTIONS, UNIFICATION & INTRODUCTION TO NEURAL NETWORKS
### 1. GENERAL LEARNING FRAMEWORK
#### Objective (Page 1)
- minΣL(wᵀxᵢ, yᵢ)+R(w)
Where:
- L→loss function
- R(w)→regularizer
---
### 2. CLASSIFICATION GOAL
#### Setup
- Dataset:
  {(x₁,y₁), ..., (xₙ,yₙ)}
- yᵢ ∈ {−1, +1}
#### Ideal Objective
- minΣ1(h(xᵢ) ≠ yᵢ)
#### Problem
- NP-hard to optimize
---
### 3. LOSS FUNCTION VIEW
#### Idea
- Replace 0–1 loss with surrogate loss
#### Form
- L(w, (x,y)) = function of (wᵀx, y)
---
### 4. COMMON LOSS FUNCTIONS
#### (a) 0–1 Loss
- L = 1(y wᵀx<0)
#### Issue
- Non-convex, hard to optimize
#### (b) Squared Loss
- L = (g(x)−y)²
#### Used in
- Regression
#### (c) Hinge Loss (SVM)
- L = max(0,1−y wᵀx)
#### (d) Logistic Loss
- L = log(1+e<sup>−y wᵀx</sup>)
#### (e) Exponential Loss (Boosting)
- L = e<sup>−y h(x)</sup>
---
### 5. KEY INSIGHT
#### Observation (Page 4)
- All losses approximate 0–1 loss
#### Property
- Convex → easier optimization
---
### 6. SVM REVISITED
#### Objective
- min (1/2)||w||² + CΣmax(0, 1−y wᵀx)
#### Interpretation
- Regularization + hinge loss
---
### 7. LOGISTIC REGRESSION REVISITED
#### Objective
- min Σ log(1+e<sup>−y wᵀx</sup>)
#### Insight
- Smooth approximation to 0–1 loss
---
### 8. PERCEPTRON AS LOSS MINIMIZATION
#### Update Rule
- w ← w + yx
#### Interpretation (Page 5)
- SGD on hinge-like loss
---
### 9. BOOSTING AS LOSS MINIMIZATION
#### Loss
- L = e<sup>−y h(x)</sup>
#### Insight
- AdaBoost minimizes exponential loss
---
### 10. UNIFICATION
#### Big Picture
- All algorithms = minimizing:
  Σ L(yᵢ, wᵀxᵢ)
#### Difference
- Choice of loss function
---
### 11. NEURAL NETWORKS — INTRODUCTION
#### Basic Model (Page 1)
- Input:
  x∈ℝᵈ
- Output:
  sign(wᵀx)
#### Limitation
- Only linear
---
### 12. MULTI-LAYER NETWORK
#### Structure
- Input layer
- Hidden layers
- Output layer
#### Hidden Layer Computation
- z = wᵀx
- a(z) = activation function
---
### 13. ACTIVATION FUNCTIONS
#### Examples (Page 1)
- Sigmoid:
  a(z) = 1/(1+e<sup>−z</sup>)
- ReLU:
  a(z) = max(0, z)
---
### 14. NETWORK OUTPUT
#### Form
- ŷ = Σ w<sub>i</sub><sup>(out)</sup> a(w<sub>i</sub><sup>(in)</sup> x)
#### Insight
- Non-linear function approximation
---
### 15. TRAINING NEURAL NETWORKS
#### Objective (Page 2)
- min Σ (NN(xᵢ) − yᵢ)²
#### Method
- Gradient Descent
---
### 16. BACKPROPAGATION
#### Idea (Page 2)
- Compute gradients using chain rule
#### Use
- Efficient parameter updates
---
### 17. KEY PROPERTY
#### Optimization
- Non-convex problem
#### Result
- Converges to local minima
---
### 18. PROBABILISTIC OUTPUT
#### Sigmoid Output
- P(y=1|x)
#### Loss
- Cross-entropy loss
---
### 19. MODERN EXTENSIONS
#### Mentioned (Page 2)
- CNN
- RNN
- LSTM
- Transformers
---
### 20. FINAL INSIGHTS
#### Core Ideas
- Learning = loss minimization + regularization
- Different models = different loss functions
- Neural networks = non-linear function learners
- Optimization via gradient descent
---
### MEMORY LINES
#### Quick Recall
- minΣL+R(w)
- Hinge: max(0, 1−y wᵀx)
- Logistic: log(1+e⁻ʸʷᵀˣ)
- Boosting: e⁻ʸʰˣ
- NN = layered function
- Backprop = chain rule
---
