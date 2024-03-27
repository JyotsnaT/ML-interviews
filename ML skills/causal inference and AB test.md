# Causal inference and A/B testing
## Introduction to causality
- Terminologies
  - Treatment intake for unit i
$$T_i = {1 \text{  if unit i recieved the treatment}, 0 \text{ if not}}$$
$$Y_i \text{is the observed outcom for unit i}$$

  - Issue with causal inference -  the same unit cannot be obeseved with or without treatment.
  - Potential outcomes : Factual - the one that happened. Counterfactual - the one that did not happen.
    $$Y_{0i} : \text{Potential outcome for unit i without treatment}$$
    $$Y_{1i} : \text{Potential outcome for unit i with treatment}$$
  - $Y_{1i}$ is currently defined but has not happened yet hence it a counterfactual outcome.
  - Individual treatment effect : $Y_{1i} - Y_{0i}$. Since we can never observe both values for one unit $i$, this value is hard to obtain.
  - Average treatment effect : $ATE = E[Y_1-Y_0]$
  - Average treatment effect on the treated : $ATT = E[Y_1-Y_0|T=1]$



# References
1. [Causal inference for the brave and true](https://matheusfacure.github.io/python-causality-handbook/landing-page.html)
