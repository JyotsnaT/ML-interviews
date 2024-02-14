# Facebook Field Guide to Machine Learning video series

## Problem Definition
- Going from business problem to machine learning task
- More often the problem is either a prediciton problem, a classification problem. 


## Data
Building datasets
For e.g list of impressions, clicks, features
Key areas to pay attention to 
- Data recency and real time training
- Training/prediction consistency
- Records and sampling
Data is rarely iid

## Evaluation
How do we define success
Offline evalautaion
- use offlien evalaution untill you have viable candidate
- Evaluate model on test set
- Have a baseline which is the simplest possible model for future work
- SPlit the data into threwe sets
  - Training sets
  - Evalaution set -
    - Traditionally random split was done followed by k-fold cross validation
    - SPlit the data in time
  - Test set - Not to be used either during training or validation

Online experimentation
- use online expeirments when there is a viable candidate

## Features
Feature should be releveant ot the model and  easier to interpret by the model
Classes of features
Categorical - k out of n encoding, continuous or derived features
  CTR of the user
Feature leakage
  - Edge cases
Feature coverage



## Models
Data -> Features -> Model -> Evaluate cycle
1. Pick a model
Interrpretability and ease to debug

3. Tune the model
4. Compare the model
Understanding the bias variance trade off
More opaque or transparent models

- hyperparameters
- Model architectures settings
    - Feature interaction
    - Number/type/width of layers
 
Efficiency : 
Transparency : Reproducability
Automation : 
Apples to apples comparison : 
## Experimentation
How to create impact

