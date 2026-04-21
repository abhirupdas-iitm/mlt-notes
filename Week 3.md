## WEEK 3 — CLUSTERING & LLOYD’S ALGORITHM (K-MEANS)
### 1. UNSUPERVISED LEARNING — CLUSTERING
#### Goal
- Given dataset:
  D = {x₁, x₂, ..., xₙ}
- Partition data into groups (clusters)
#### Idea
- Points in same cluster → similar
- Points in different clusters → dissimilar :contentReference[oaicite:0]{index=0}
---
### 2. PROBLEM FORMULATION
#### Input
- Data points:
  x₁, x₂, ..., xₙ ∈ ℝᵈ
#### Output
- Cluster assignments:
  z₁, z₂, ..., zₙ where zᵢ ∈ {1, 2, ..., K}
#### Cluster Means
- For cluster k:
  μₖ = (1 / |Cₖ|) Σ xᵢ  where i ∈ Cₖ
---
### 3. OBJECTIVE FUNCTION (K-MEANS)
#### Goal
Minimize total within-cluster variance:
F(z₁, ..., zₙ) = Σ Σ ||xᵢ − μₖ||²  
                       k     i ∈ Cₖ
#### Interpretation
- Minimize distance of points from their cluster centers
#### Important Insight
- This optimization problem is **NP-hard**
---
### 4. LLOYD’S ALGORITHM (K-MEANS)
#### Initialization
- Choose initial cluster assignments OR initial means
---
#### Iterative Steps
Repeat until convergence:
##### Step 1: Compute Means
- For each cluster k:
  μₖ = (1 / |Cₖ|) Σ xᵢ
##### Step 2: Re-assignment
- For each point xᵢ:
  zᵢ = argminₖ ||xᵢ − μₖ||²
---
### 5. KEY PROPERTY — OBJECTIVE DECREASES
#### Insight (Pages 4–6)
- Each step **never increases** objective F
##### Why?
- Mean minimizes squared distance within cluster
- Assignment step chooses closest cluster
#### Result
- F(z) decreases monotonically
---
### 6. CONVERGENCE OF LLOYD’S ALGORITHM
#### Question
- Does the algorithm converge?
#### Answer
- YES
#### Reason
- Finite number of possible assignments
- Objective strictly decreases or stays same
- Must terminate eventually
#### Important Note
- Converges to **local minimum**, not necessarily global
---
### 7. NATURE OF CLUSTERS
#### Observation (Pages 8–10)
- Clusters are defined by:
  ||x − μ₁||² ≤ ||x − μ₂||²
#### Result
- Decision boundary between clusters is:
  Linear (hyperplane)
#### Insight
- K-means produces **Voronoi regions**
---
### 8. GEOMETRIC INTERPRETATION
#### From Diagrams (Pages 9–10)
- Each cluster corresponds to a region in space
- Boundaries are perpendicular bisectors
#### For K = 2
- Single separating hyperplane
#### For K = 3
- Multiple regions intersecting
---
### 9. LIMITATIONS OF K-MEANS
#### Cluster Shape
- Works best for:
  - Spherical clusters
  - Equal variance
#### Issues
- Fails for:
  - Non-convex clusters
  - Different densities
---
### 10. INITIALIZATION
#### Problem
- Result depends on starting points
#### Methods
- Random initialization
- K-means++
#### K-means++ Idea
- Spread initial means apart
- Improves convergence
---
### 11. CHOICE OF K
#### Problem
- How many clusters?
#### Objective Trade-off
- Increasing K → reduces error
- But leads to overfitting
---
### 12. MODEL SELECTION METHODS
#### Elbow Method (Page 14)
- Plot objective vs K
- Choose point where decrease slows
#### Information Criteria
- AIC (Akaike Information Criterion)
- BIC (Bayesian Information Criterion)
---
### 13. GUARANTEE (K-MEANS++)
#### Insight (Page 16)
- Expected objective is bounded:
  E[ Σ ||xᵢ − μₖ||² ] ≤ O(log K) × optimal
#### Meaning
- Near-optimal solution in expectation
---
### 14. FINAL INSIGHTS
#### Core Ideas
- Clustering = partitioning data
- Objective = minimize intra-cluster variance
- Lloyd’s algorithm = iterative refinement
- Converges but only locally optimal
---
### MEMORY LINES
#### Quick Recall
- zᵢ = cluster assignment
- μₖ = cluster mean
- minimize Σ ||x − μ||²
- assignment + update loop
- converges to local minimum
---
