# Grokking the Machine Learning Interview

## The rise of Machine Learning
ML is used at several areas like speech understanding, visual understansing, search ranking, fraud detection

## ML interview expectation

  <img src="/ML system design/MLsystemdesign.png" width = 700>

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

  <img src="/ML system design/serach_architecture.png" width=500/>

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

 ## Performance and capacity considerations
 - Capacity considerations to be made during
     - Training : Training data, model capacity
     - Evalaution : serving SLA, model capacity
 - Types of complexities
     - Training : Time taken to train the model
     - Evaluation : Time taken to evaluate input at testing time
     - Sample : Number of examples requried to succesfully learn target function
  - Asymptotc analysis
    - Linear/Logistic regression : Train - O(nfe), Eval - O(f), Best choise to save on train and  evaluation time
    - Neural Networks : Train : NA, Eval - O(fnl1 + nl1nl2 + nl2nl3 .. ). Best choise to solve complex problems and if complexity is not an issue.
    - Decision trees/forest : Train : O(nfn_td), Eval : O(fn_td). It is faster than Deep networks and generalizes well. Should be preferred when training data is scarce and capacity is crucial.
  - Example
    - No. of documents in the search engine to evaluate against a query : 100M = 100 X $10^6$
    - SLA 
      - Performance : Return the results back within given time frame
      - Capacity : Queries per second the system can handle
    - Tree based model :
      - Inference time = $1\mu s$ = 1 X $10^{-6}s$
      - Total for 100M images = 100s
    - Load distribution :
      - Distribute load of one query among 1000 shards
      - Inference time for 100M images - 100 X $10^6$ X 1 X $10^{-6}$ X $10^{-3}$ s = 100ms
    - Deep learning model :
      - Inference time = 1ms = $10^{-3}s$
        - Total time with 1000 shards = 100 X $10^6$ X $10^{-3}$ X $10^{-3}$ s = 100s
        - For unlimited capacity, just add more shards till this numnber is down. But it is not practical
  - Funnel based approach
    In this method we begin with a simpler and fast model to first narrow down our search to small number of items. Then apply the more complex model on limited set of items which reduces the SLA time overall
    - Example :
      - Deep learning on 500 documents with 5 shards : 500 X $10^-3$ X $5^-1$ s = 100ms 

## Training data collection strategies
- Main components of ML system - ML algorithm, Training data, Features
- Quality and quantity of trainig data impact the final performance greatly
- Collection techniques
    - Online data collection :
        - If there is an existing system in place which gives model predictions, then user interaction with those can be treated as training data.          - This can be a rule based or a weak ML system.
        - Ex. Recommendation system, an existing rule based recommender, popularity recommender, region based recommender would be existing. USer's interaction with those can be treated as training data.
    - Offline data collection :
        - Use labellers to generate high quality data
        - Ex. Image segmentation : We need different components of the data to be labelled for this task.
            - Crowdsourcing : Get labels by outsourcing tasks to group of people Works for simpler tasks. Does not work when there are privacy concerns, or there are complex tasks.
            - Specialized labellers : Trained labellers for the speicialized task. Has a high training time for labellers. Might be expensive
            - Open source datasets
    - Additional creative collection strategies
