---
title: "Propensity score"
excerpt: "Unraveling Causal Effects Using Propensity Score: A Python Guide"
categories:
  - portfolio
tags:
  - data science
  - python
  - causal inference

---
### What is Propensity Score?

The propensity score is the probability of a unit (e.g., a person, a company) being assigned to a particular treatment given a set of observed covariates. It is used to balance the distribution of observed covariates between treated and control groups in observational studies, helping to reduce bias when estimating causal effects.

Formally, for a binary treatment \( T \) and a set of covariates \( X \), the propensity score \( e(X) \) is defined as:
\[ e(X) = P(T = 1 | X) \]

### Using Propensity Scores for Causal Inference

#### Steps to Implement Propensity Score Methods

1. **Estimate Propensity Scores**:
   Use logistic regression or another suitable model to estimate the probability of treatment assignment based on observed covariates.

2. **Check Overlap**:
   Ensure that there is common support, meaning that for all values of the propensity score, there are both treated and control units.

3. **Balance Covariates**:
   Assess whether the covariates are balanced between treated and control groups after matching, weighting, or stratifying on the propensity score.

4. **Estimate Treatment Effect**:
   Use the propensity scores to adjust for confounding and estimate the causal effect of the treatment.

### Common Methods Using Propensity Scores

1. **Matching**:
   Pair treated units with control units that have similar propensity scores.

2. **Stratification**:
   Divide the sample into strata (e.g., quintiles) based on propensity scores and compare outcomes within each stratum.

3. **Inverse Probability Weighting (IPW)**:
   Weight units by the inverse of their probability of receiving the treatment they actually received to create a pseudo-population in which the treatment is independent of covariates.

4. **Covariate Adjustment**:
   Include the propensity score as a covariate in regression models.

### Example: Using Propensity Score Matching in Python

#### Step 1: Estimating Propensity Scores

```python
import pandas as pd
from sklearn.linear_model import LogisticRegression

# Example data
data = {
    'treated': [1, 1, 0, 0, 1, 0, 1, 0, 1, 0],
    'age': [23, 45, 31, 35, 40, 25, 50, 48, 37, 28],
    'income': [50000, 80000, 60000, 55000, 75000, 52000, 85000, 70000, 72000, 51000]
}
df = pd.DataFrame(data)

# Covariates
X = df[['age', 'income']]
# Treatment indicator
T = df['treated']

# Logistic regression to estimate propensity scores
logistic = LogisticRegression()
logistic.fit(X, T)
df['propensity_score'] = logistic.predict_proba(X)[:, 1]
```

#### Step 2: Matching

```python
import numpy as np
from sklearn.neighbors import NearestNeighbors

# Define the treatment and control groups
treated = df[df['treated'] == 1]
control = df[df['treated'] == 0]

# Nearest neighbors matching on propensity score
nn = NearestNeighbors(n_neighbors=1)
nn.fit(control[['propensity_score']])
distances, indices = nn.kneighbors(treated[['propensity_score']])

# Matched control units
matched_controls = control.iloc[indices.flatten()]

# Combine treated and matched control units
matched_df = pd.concat([treated, matched_controls])
```

#### Step 3: Assess Balance

Check if covariates are balanced between treated and control groups in the matched sample.

```python
print(matched_df.groupby('treated').mean())
```

#### Step 4: Estimate Treatment Effect

Calculate the average treatment effect on the outcome using the matched sample.

```python
# Example outcome data
matched_df['outcome'] = [1, 0, 1, 1, 0, 0, 1, 0]

# Average treatment effect on the treated (ATT)
att = matched_df[matched_df['treated'] == 1]['outcome'].mean() - \
      matched_df[matched_df['treated'] == 0]['outcome'].mean()
print("ATT:", att)
```

### Conclusion

Propensity scores are a powerful tool for addressing confounding in observational studies, enabling researchers to estimate causal effects more reliably. By estimating the probability of treatment assignment given covariates, and using methods such as matching, stratification, inverse probability weighting, or covariate adjustment, researchers can create balanced comparison groups and reduce bias in their estimates of treatment effects.

[Python Example: NSW Job Training](https://github.com/chaix026/Causal-Inference/blob/main/Propensity%20Score.ipynb){: .btn .btn--success .btn--large}  


