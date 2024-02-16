# Grokking the Machine Learning Interview

## The rise of Machine Learning
ML is used at several areas like speech understanding, visual understansing, search ranking, fraud detection

## ML interview expectation
<img src="ML system design/MLsystemdesign.png" width=400/>

## Setting up ML system
- Setting up problem
  - Narrow the problem space
  - chalk out the requiements of the system
For e.g.
> PS: "Design a search engine to display most relevant results in response to user's queires".

Probe: What kind of queries can it answer? What kind of search is it? Generic or specialized?

> PS: "Build a generic search engine that returns relevant results for queries like “Richard Nixon”, “Programming languages” etc."

Probe: How is the feed currently displayed and how can can it be improved?

> PS: "Given a list of tweets, train an ML model that predicts the probability of engagement of tweets and orders them based on that score."

- Understanding scale and latency requqirements
  - Latency : "How fast do we want the results to the query"
  - Scale : "How many requests per second?", "How many websites to retrieve?"

- Metrics definition
  - Offline metrics
    - Classification: accuracy, logloss, precision, recall, F1 score
    - Search and ranking: NDCG 
  - Online metrics
    - Component wise metrics
    - End-to-end metrics
  
- Architecture design
<img src="ML system design/serach_architecture.png" width=500/>

- Scale consideration
  Funnel method can be used to reduce the number of items at every stage, and a complex model can be safely used in final stages.

- Offline model building
  - Train data generation
    - Human labelled data : It is an expensive method
    - Open source datasets
    - Data collection through user interaction with pre-existing systems
  - Feature Engineering
    - Start by pinpointing actors given at hand. For e.g. in case of movie recommendation the actors are logged in user, movies available, context
    - To make features, individually inspect the actors. For e,g, users can give user age, gender, language, etc.
    - Historical engagement between actors can lead to another set of features.
  - Model training
    - In the funnel approach, using the simpler models at the top of the funnel and more complex models at the bottom of the funnel.
    - Pre-trained SOTA for transfer learning
  - Offline evaltuation
    - Train, validation and test split
    - fix on types of models, hyperparamets
    - select top models based on offline metrics selected earlier
- Online Model execution and evaluation
  - Test the top performing models in online environment
  - Online metrics performance decide whether the model is fit to be deployed.
- Iterative model development
  - Debug the model when the online performance does not replicate the offline testing.
  - Monitor the performance of the first version of the model after it has been deployed.
  - 
