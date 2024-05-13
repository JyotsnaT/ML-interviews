# Industrial papers related to key problem areas

# [The Importance of Being Causal](https://hdsr.mitpress.mit.edu/pub/wjhth9tr/release/3)

Abstract
  - Causal inferene is the study of understanding how actions, interventions and treatment affect outcomes of interest.
  - Randomized experiments is a common way to establish causation but it might not always be feasible.
  - We can extract causal estimates from observational data called observational study methods.

Introduction
  - Identifying impactful opportunities can be done by forecasting impact of an opportuninty known as opportuninty sizing and understanding of ecosystem.
  - This involves retrispective analysis of afffect of an innovation on the business outcome.
  - "the ability to randomize treatment assignment ensures that observed differences in outcomes between treatments are due to the intervention "
  - Randomized experiments are not always feasible which leads to biased estimates of opportunity sizing and ecosystem insights.
  - Observations causal inference : Derive causal claims from observational data.
  - Extremes in observation causal inference
    - Retrospective justification of decision, might lead to building false confidence.
    - Lack of observational data to nullify innovation, current data might not capture the effects
  - Observational causal inference is not replacement for actual experimentation. However it enhances the experiments and improve decision making capabilities.
  - Description vs prediction vs causal inferene : How interventions impact the outcome instead of predictions in static world.

LinkedIn case studdies
  - Analysis template
   - First: Describe business use case and establish why observational causal study is important
   - Second : Naive estimation strategy
   - third : Explain choice of causal method
   - fourth : Insights from analysis
  - For the causal questions, observational causal inference can be used in the following scenarios -
    - Opportunity sizing : Identify if a treatment is a good opportunity out of a set of candidates.
    - Ecosystem insights : Analyzing all aspecet of a natural firm operations.
    - Uncontrolled rollout : When release process of innovations is out of control.
  - Input categories for data : Cross sectional, interrupted time series, panel, instrumental variable
  - Robustness of findings should be tested through sensitivity analysis

Case study 1 : LinkedIn Job postings, Opportunity sizing
- Having some job listing fields mandatory so job seekers have all relevant information such as jobtitle, location, function, industry or employment type.
- Business metric getting traked - view-to-apply rate. Treatment is to either have or not have these attributes, we pick jobtitle for simplicity.
- Naive estimate measure differene between the metrics obtained for job where a jobtitle exists vs one where it does not exist. It can be inaccurate because of the presence of confounders. One likely case is, people view the well know company job postings more who are also likely to have a job title.
- In this a job's attribute is assigned during job creation hence it falls in the cross section study category.
- In a cross sectional study, covariates collection, treatmemt assignment and outcome analysis happen in sequnce for each unit. The methods are usually divided into a design phase and analysis phase.
- The units should be alike in all means but should differ only in treatment they recieve.
- In this oppportunity sizing analysis is was estimated that having a jobtitle has 2% more improvement over the metrics
