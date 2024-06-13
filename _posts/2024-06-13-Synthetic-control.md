---
title: "Synthetic Control"
excerpt: "Synthetic Control for Causal Inference"
categories:
  - portfolio
tags:
  - data science
  - python
  - causal inference

---
### What is Synthetic Control for Causal Inference?

Synthetic control is a method used in causal inference to estimate the effect of an intervention or treatment when a traditional randomized controlled trial is not feasible. It is particularly useful in observational studies where the treatment is applied to a single unit (e.g., a country, a state, a company) and there is no obvious control group for comparison.

The basic idea is to construct a "synthetic" control group by taking a weighted combination of untreated units (e.g., other countries, states, or companies) that approximates the characteristics of the treated unit before the intervention. The effect of the intervention is then estimated by comparing the post-intervention outcomes of the treated unit with the outcomes of the synthetic control.

### Key Steps in Synthetic Control

1. **Selection of Donor Pool**: Identify a set of potential control units (the donor pool) that did not receive the treatment.
2. **Pre-Treatment Matching**: Use a weighted combination of the units in the donor pool to construct a synthetic control that closely matches the treated unit on pre-treatment characteristics and outcomes.
3. **Estimation of Treatment Effect**: Compare the post-treatment outcomes of the treated unit with the synthetic control to estimate the causal effect of the intervention.

### Example of Synthetic Control in Python

#### Step 1: Prepare the Data

Let's assume we have a dataset with pre-treatment and post-treatment outcomes for one treated unit and several control units.

```python
import pandas as pd
import numpy as np

# Example data: Pre-treatment and post-treatment outcomes for one treated unit and several control units
data = {
    'unit': ['treated', 'control_1', 'control_2', 'control_3'],
    'pre_1': [2, 1, 3, 2],
    'pre_2': [3, 2, 4, 3],
    'pre_3': [4, 3, 5, 4],
    'post': [5, 3, 6, 4]
}
df = pd.DataFrame(data)

# Split into treated and control units
treated = df[df['unit'] == 'treated']
controls = df[df['unit'] != 'treated']
```

#### Step 2: Construct Synthetic Control

We need to find weights for the control units that minimize the difference between the treated unit and the weighted combination of controls in the pre-treatment period.

```python
from sklearn.linear_model import LinearRegression

# Pre-treatment outcomes for controls
X_pre = controls[['pre_1', 'pre_2', 'pre_3']].values
# Pre-treatment outcomes for treated unit
y_pre = treated[['pre_1', 'pre_2', 'pre_3']].values.flatten()

# Fit regression model to find weights
model = LinearRegression(fit_intercept=False)
model.fit(X_pre.T, y_pre)
weights = model.coef_

# Create synthetic control
synthetic_control = np.dot(weights, X_pre)
```

#### Step 3: Estimate Treatment Effect

Compare the post-treatment outcome of the treated unit with the synthetic control.

```python
# Post-treatment outcomes
post_treated = treated['post'].values[0]
post_synthetic = np.dot(weights, controls['post'].values)

# Estimate treatment effect
treatment_effect = post_treated - post_synthetic
print("Estimated Treatment Effect:", treatment_effect)
```

### Conclusion

The synthetic control method is a powerful tool for causal inference in observational studies, especially when dealing with a single treated unit. By constructing a synthetic control from a combination of untreated units that closely resembles the treated unit in the pre-treatment period, researchers can estimate the causal effect of an intervention more reliably.

### Advantages and Limitations

#### Advantages

1. **Flexibility**: Can be used when traditional randomized controlled trials are not feasible.
2. **Transparency**: Provides a clear method for constructing a control group and estimating treatment effects.
3. **Applicability**: Useful in various fields, including economics, political science, and public health.

#### Limitations

1. **Complexity**: Requires careful selection of donor pool and pre-treatment variables.
2. **Sensitivity**: Results can be sensitive to the choice of donor pool and the method used to construct the synthetic control.
3. **Data Requirements**: Requires rich data on pre-treatment characteristics and outcomes to construct a reliable synthetic control.

[Python Example: California Tobacco Tax and Health Protection Act](https://github.com/chaix026/Causal-Inference){: .btn .btn--success .btn--large}  


