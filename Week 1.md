## WEEK 1 — UNSUPERVISED LEARNING & PRINCIPAL COMPONENT ANALYSIS (PCA)
### 1. UNSUPERVISED LEARNING — REPRESENTATION
#### Goal
- Given a dataset:
  D = {x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>}
- Learn something **useful / meaningful** about the data
#### Key Idea
- Data points → vectors in ℝ<sup>d</sup>
- Find a better **representation** of data
#### Running Theme
- Compress / represent data efficiently while preserving information :contentReference[oaicite:0]{index=0}
---
### 2. PROBLEM FORMULATION
#### Input
- Dataset:
  D = {x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>}, where x<sub>i</sub> ∈ ℝ<sup>d</sup>
#### Output
- A “compressed” or lower-dimensional representation
#### Question
- How do we represent data using fewer dimensions?
---
### 3. INTUITION — PROJECTION
#### Idea
- Project data onto a direction w
#### Projection Formula
- Projection of x onto w:
  proj<sub>w</sub>(x) = (x<sup>T</sup>w) w
#### Interpretation
- Replace each data point with its projection
#### From Diagram (Page 4)
- All points “collapse” onto a line along w
- We retain maximum structure along that direction
---
### 4. RECONSTRUCTION & ERROR
#### Reconstruction
- Approximate x using projection:
  x̂ = (x<sup>T</sup>w) w
#### Error
- Difference between original and reconstructed:
  e = x − x̂
#### Insight (Page 5)
- Projection keeps **important information**
- Error represents **lost information**
---
### 5. OBJECTIVE FUNCTION
#### Goal
- Find best direction w
#### Dataset Error
- Define loss:
  F(w) = (1/n) Σ ||x<sub>i</sub> − (x<sub>i</sub><sup>T</sup>w)w||<sup>2</sup>
#### Constraint
- ||w||<sup>2</sup> = 1
---
### 6. OPTIMIZATION REFORMULATION
#### Key Result
Minimizing reconstruction error is equivalent to:
- Maximizing variance:
  max<sub>||w||=1</sub> (1/n) Σ (x<sub>i</sub><sup>T</sup>w)<sup>2</sup>
#### Matrix Form
- Let:
  C = (1/n) Σ x<sub>i</sub> x<sub>i</sub><sup>T</sup>
Then:
- max w<sup>T</sup> C w
---
### 7. EIGENVECTOR SOLUTION
#### Optimization Problem
- max w<sup>T</sup> C w
- subject to ||w|| = 1
#### Solution
- w = eigenvector of C corresponding to largest eigenvalue λ<sub>1</sub>
#### Insight (Page 20)
- λ = w<sup>T</sup> C w → variance captured
---
### 8. FIRST PRINCIPAL COMPONENT
#### Definition
- w<sub>1</sub> = argmax<sub>||w||=1</sub> w<sup>T</sup> C w
#### Meaning
- Direction of **maximum variance**
#### Projection
- New coordinate:
  z<sub>i</sub> = x<sub>i</sub><sup>T</sup> w<sub>1</sub>
---
### 9. RESIDUALS (AFTER FIRST COMPONENT)
#### Definition
- Residual:
  r<sub>i</sub> = x<sub>i</sub> − (x<sub>i</sub><sup>T</sup>w<sub>1</sub>)w<sub>1</sub>
#### Insight (Page 14)
- Residual contains information not captured by w<sub>1</sub>
---
### 10. SECOND PRINCIPAL COMPONENT
#### Goal
- Find w<sub>2</sub> that maximizes variance of residuals
#### Constraint
- w<sub>2</sub><sup>T</sup> w<sub>1</sub> = 0
#### Meaning
- Orthogonal to first component
---
### 11. GENERAL PCA PROCEDURE
#### Iterative Process
- Find:
  w<sub>1</sub>, w<sub>2</sub>, ..., w<sub>d</sub>
#### Properties
- w<sub>i</sub><sup>T</sup> w<sub>j</sub> = 0 (orthogonality)
- ||w<sub>i</sub>|| = 1
#### Result
- Orthonormal basis
---
### 12. FULL RECONSTRUCTION
#### Expression
- Each data point:
  x<sub>i</sub> = Σ (x<sub>i</sub><sup>T</sup>w<sub>k</sub>) w<sub>k</sub>
#### Insight (Page 16)
- Data expressed in terms of principal components
---
### 13. DIMENSIONALITY REDUCTION
#### Idea
- Keep only top k components
#### Approximation
- x<sub>i</sub> ≈ Σ<sub>k</sub> (x<sub>i</sub><sup>T</sup>w<sub>k</sub>) w<sub>k</sub>
#### Trade-off
- Less dimensions ↔ some information loss
---
### 14. GEOMETRIC INTERPRETATION
#### From Diagrams (Pages 4, 22, 23)
- PCA finds directions where:
  - Data is most spread out
  - Noise is minimized
#### Signal vs Noise
- Principal components → signal directions
- Residual directions → noise
---
### 15. VARIANCE INTERPRETATION
#### Eigenvalue Meaning
- λ<sub>k</sub> = variance captured by w<sub>k</sub>
#### Ordering
- λ<sub>1</sub> ≥ λ<sub>2</sub> ≥ ... ≥ λ<sub>d</sub>
---
### 16. CENTERING DATA (IMPORTANT)
#### Requirement
- Mean of dataset must be zero:
  (1/n) Σ x<sub>i</sub> = 0
#### Why
- Ensures PCA captures variance correctly
---
### 17. FINAL INSIGHT
#### What PCA Does
- Finds new coordinate system
- Aligns axes with directions of maximum variance
- Removes redundancy
#### Example (Page 23)
- Height + weight → PCA finds combined informative direction
---
### 18. FINAL TAKEAWAYS
#### Core Ideas
- PCA = projection + variance maximization
- Uses eigenvectors of covariance matrix
- Orthogonal components
- Enables dimensionality reduction
---
### MEMORY LINES
#### Quick Recall
- proj = (x<sup>T</sup>w)w
- C = (1/n)XX<sup>T</sup>
- max w<sup>T</sup>Cw
- eigenvector = principal component
- λ = variance
---
