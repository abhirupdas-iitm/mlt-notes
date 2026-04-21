## WEEK 2 — PCA LIMITATIONS, KERNEL METHODS & KERNEL PCA

### 1. ISSUES / CONCERNS WITH PCA
#### Core Limitation
- PCA captures **linear relationships only**
- Fails when data lies on a **non-linear manifold**
#### Example Insight
- Data may appear non-linearly separable in original space
- But can become linearly separable in a transformed space
#### Time Complexity Issue
- Computing covariance matrix:
  C = (1/n) X X<sup>T</sup>
- Eigen decomposition becomes expensive when:
  - Dimension d is very large
#### High Dimensional Issue
- If X ∈ ℝ<sup>d×n</sup> and d >> n:
  - Computing eigenvectors of C ∈ ℝ<sup>d×d</sup> is inefficient
---
### 2. KEY IDEA — FEATURE TRANSFORMATION
#### Motivation
- Map data to a higher-dimensional space:
  φ : ℝ<sup>d</sup> → ℝ<sup>D</sup>, where D >> d
#### Goal
- Transform features such that:
  - Non-linear structure becomes linear
#### Insight
- Instead of working in original space:
  x → φ(x)
---
### 3. FEATURE MAPPING EXAMPLES
#### Quadratic Mapping
- For x = [f<sub>1</sub>, f<sub>2</sub>]
- φ(x) = [f<sub>1</sub><sup>2</sup>, f<sub>2</sub><sup>2</sup>, √2 f<sub>1</sub>f<sub>2</sub>]
#### Cubic Mapping (General Idea)
- φ(x) includes:
  - Linear terms
  - Quadratic terms
  - Cubic terms
#### Dimensional Explosion
- For degree p:
  Number of features grows combinatorially
#### Problem
- Explicitly computing φ(x) becomes infeasible
---
### 4. INNER PRODUCT TRICK (CRITICAL INSIGHT)
#### Observation
- Many algorithms depend only on:
  φ(x)<sup>T</sup> φ(z)
#### Key Idea
- Compute inner product **without explicitly computing φ(x)**
---
### 5. POLYNOMIAL KERNEL
#### Definition
- K(x, z) = (x<sup>T</sup>z + 1)<sup>p</sup>
#### Insight
- Equivalent to:
  φ(x)<sup>T</sup> φ(z)
#### Example (p = 2)
- K(x, z) = (x<sup>T</sup>z + 1)<sup>2</sup>
- Expands to include:
  - f<sub>1</sub><sup>2</sup>, f<sub>2</sub><sup>2</sup>, f<sub>1</sub>f<sub>2</sub>, etc.
#### Key Takeaway
- High-dimensional mapping computed **implicitly**
---
### 6. RADIAL BASIS FUNCTION (RBF) KERNEL
#### Definition
- K(x, z) = exp( - ||x − z||<sup>2</sup> / (2σ<sup>2</sup>) )
#### Interpretation
- Measures similarity based on distance
#### Insight
- Corresponds to **infinite-dimensional feature space**
---
### 7. KERNEL FUNCTION (GENERAL)
#### Definition
- A function:
  K : ℝ<sup>d</sup> × ℝ<sup>d</sup> → ℝ
#### Property
- K(x, z) = φ(x)<sup>T</sup> φ(z)
#### Examples
- Polynomial Kernel
- RBF Kernel
---
### 8. VALID KERNELS — MERCER’S THEOREM
#### Condition
A function K is a valid kernel **iff**:
##### (a) Symmetry
- K(x, z) = K(z, x)
##### (b) Positive Semi-Definite
- For any vector α ∈ ℝ<sup>n</sup>:
  Σ Σ α<sub>i</sub> α<sub>j</sub> K(x<sub>i</sub>, x<sub>j</sub>) ≥ 0
#### Equivalent Statement
- Kernel matrix K must have:
  - All eigenvalues ≥ 0
---
### 9. REVISITING PCA (LINEAR ALGEBRA FORM)
#### Data Matrix
- X = [x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>]
#### Covariance Matrix
- C = (1/n) X X<sup>T</sup>
#### Eigenvalue Problem
- C w = λ w
#### Key Insight
- Principal components = eigenvectors of C
---
### 10. DUAL FORMULATION OF PCA
#### Key Result
- Eigenvectors can be written as:
  w = X α
#### Substituting into eigen equation:
- C w = λ w
- (1/n) X X<sup>T</sup> X α = λ X α
#### Multiply by X<sup>T</sup>:
- X<sup>T</sup> X X<sup>T</sup> X α = nλ X<sup>T</sup> X α
#### Define:
- K = X<sup>T</sup> X
#### Final Form:
- K α = nλ α
#### Insight
- Solve eigenproblem using K ∈ ℝ<sup>n×n</sup> instead of C ∈ ℝ<sup>d×d</sup>
---
### 11. KERNEL PCA — CORE IDEA
#### Motivation
- Perform PCA in feature space φ(x)
#### Problem
- Cannot compute φ(x) explicitly
#### Solution
- Use kernel trick:
  K<sub>ij</sub> = φ(x<sub>i</sub>)<sup>T</sup> φ(x<sub>j</sub>)
---
### 12. KERNEL PCA ALGORITHM
#### Input
- Dataset: {x<sub>1</sub>, ..., x<sub>n</sub>}
#### Step 1: Compute Kernel Matrix
- K<sub>ij</sub> = K(x<sub>i</sub>, x<sub>j</sub>)
#### Step 2: Center the Kernel Matrix
- K̄ = K − 1K − K1 + 1K1
Where:
- 1 = (1/n) matrix of ones
#### Step 3: Eigen Decomposition
- Solve:
  K α = λ α
#### Step 4: Normalize Eigenvectors
- Ensure:
  ||α|| = 1
#### Step 5: Projection
- Projection of x onto k-th component:
  φ(x)<sup>T</sup> w<sub>k</sub> = Σ α<sub>i</sub><sup>(k)</sup> K(x<sub>i</sub>, x)
---
### 13. IMPORTANT INSIGHT
#### We Never Compute:
- φ(x)
#### We Only Compute:
- K(x, z)
#### This Enables:
- Working in extremely high-dimensional spaces efficiently
---
### 14. FINAL TAKEAWAYS
#### Core Ideas
- PCA fails for non-linear data
- Feature mapping solves this
- Explicit mapping is expensive
- Kernel trick avoids computation
- Kernel PCA = PCA in feature space using kernels
---
### MEMORY LINES
#### Quick Recall
- φ(x) → feature mapping
- K(x, z) → inner product in feature space
- Mercer → validity condition
- K = X<sup>T</sup>X → dual PCA
- Kernel PCA → non-linear PCA
---
