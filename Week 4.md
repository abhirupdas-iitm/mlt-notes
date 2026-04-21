## WEEK 4 — PROBABILISTIC MODELS, MLE, BAYESIAN LEARNING & EM ALGORITHM
### 1. SHIFT IN PERSPECTIVE
#### Earlier Weeks
- Representation → PCA
- Clustering → K-means
#### Now
- Assume a **probabilistic model** for data
#### Goal
- Estimate unknown parameters from data
---
### 2. PROBABILISTIC MODELING
#### Idea
- Data is generated from some distribution
#### Steps
1. Assume model
2. Observe data
3. Estimate parameters
#### Example (Coin Toss)
- Data: {x₁, x₂, ..., xₙ}, xᵢ ∈ {0,1}
- Parameter: p = P(head)
---
### 3. ASSUMPTIONS
#### i.i.d Assumption
- Observations are:
  - Independent
  - Identically distributed
#### Implication
- Joint probability:
  P(x₁, ..., xₙ | θ) = ∏ P(xᵢ | θ)
---
### 4. LIKELIHOOD FUNCTION
#### Definition
- Likelihood of parameter θ:
  L(θ) = P(data | θ)
#### For Bernoulli
- L(p) = ∏ p^{xᵢ} (1−p)^{1−xᵢ}
#### Log-Likelihood
- log L(p) = Σ [xᵢ log p + (1−xᵢ) log(1−p)]
---
### 5. MAXIMUM LIKELIHOOD ESTIMATION (MLE)
#### Goal
- Find parameter maximizing likelihood:
  θ̂<sub>ML</sub> = argmax L(θ)
#### Result (Bernoulli)
- p̂ = (1/n) Σ xᵢ
#### Insight (Page 6)
- Sample mean = MLE
---
### 6. GAUSSIAN MLE
#### Model
- xᵢ ~ N(μ, σ²)
#### Likelihood
- L(μ, σ²) = ∏ N(xᵢ | μ, σ²)
#### Result
- μ̂ = (1/n) Σ xᵢ
- σ̂² = (1/n) Σ (xᵢ − μ̂)²
---
### 7. LIMITATION OF MLE
#### Issue
- No prior knowledge used
#### Insight
- Only data-driven
- Can overfit
---
### 8. BAYESIAN MODELING
#### Idea
- Treat parameters as random variables
#### Components
- Prior: P(θ)
- Likelihood: P(data | θ)
- Posterior:
  P(θ | data) ∝ P(data | θ) P(θ)
---
### 9. BAYESIAN UPDATE
#### Concept (Pages 9–11)
- Start with belief (“hunch”)
- Update using data
#### Interpretation
- Prior → belief before data
- Posterior → updated belief
---
### 10. EXAMPLE — BETA PRIOR
#### Model
- Bernoulli likelihood
- Prior: Beta(α, β)
#### Posterior
- Beta(α + Σ xᵢ, β + n − Σ xᵢ)
#### Insight
- Prior acts like pseudo-counts
---
### 11. MAP ESTIMATION
#### Definition
- θ̂<sub>MAP</sub> = argmax P(θ | data)
#### Equivalent
- Maximize:
  log P(data | θ) + log P(θ)
#### Insight
- MLE + regularization
---
### 12. MIXTURE OF GAUSSIANS (GMM)
#### Motivation (Page 1)
- Single Gaussian cannot model complex data
#### Idea
- Data generated from mixture:
  P(x) = Σ πₖ N(x | μₖ, σₖ²)
#### Parameters
- πₖ (mixing weights)
- μₖ (means)
- σₖ² (variances)
#### Constraint
- Σ πₖ = 1
---
### 13. LATENT VARIABLES
#### Hidden Variable
- zᵢ = cluster/component assignment
#### Observed
- xᵢ
#### Insight
- zᵢ not known → makes problem harder
---
### 14. LOG-LIKELIHOOD FOR GMM
#### Expression
- log L(θ) = Σ log ( Σ πₖ N(xᵢ | μₖ, σₖ²) )
#### Problem
- Cannot maximize directly (log of sum)
---
### 15. JENSEN’S INEQUALITY
#### For concave function f:
- f( Σ λₖ xₖ ) ≥ Σ λₖ f(xₖ)
#### Important Result
- log is concave
#### Use
- Helps create lower bound for likelihood
---
### 16. KEY IDEA OF EM
#### Trick
- Introduce auxiliary variables λᵢₖ
#### Result
- Lower bound on log-likelihood
#### Insight (Page 5)
- Makes optimization tractable
---
### 17. EM ALGORITHM
#### Goal
- Maximize log-likelihood iteratively
#### Step 1: E-Step (Expectation)
- Compute responsibilities:
  γᵢₖ = P(zᵢ = k | xᵢ)
#### Step 2: M-Step (Maximization)
- Update parameters:
  μₖ = Σ γᵢₖ xᵢ / Σ γᵢₖ  
  σₖ² = Σ γᵢₖ (xᵢ − μₖ)² / Σ γᵢₖ  
  πₖ = (1/n) Σ γᵢₖ
---
### 18. INTERPRETATION
#### Soft Clustering
- Each point belongs partially to clusters
#### Difference from K-means
- K-means → hard assignment
- EM → probabilistic assignment
---
### 19. CONVERGENCE
#### Property
- Log-likelihood increases every iteration
#### Result
- Converges to local maximum
---
### 20. FINAL INSIGHTS
#### Core Ideas
- MLE → data-driven estimation
- Bayesian → incorporates prior
- GMM → flexible modeling
- EM → solves latent variable problem
---
### MEMORY LINES
#### Quick Recall
- L(θ) = P(data | θ)
- θ̂ = argmax L(θ)
- Posterior ∝ likelihood × prior
- GMM = Σ πₖ N(x | μₖ, σₖ²)
- EM = E-step + M-step
---
