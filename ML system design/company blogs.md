# ML Case studies from industry

1. [AB test](#ab_test)
2. [Feed Ranking](#feed_ranking)
3. [Travel](#travel)
4. [E-commerce](#e_comm)


<a name="ab_test"></a>
# AB test
- [ ] [Measurement and analysis of ranking at Instagram](https://www.facebook.com/watch/?v=1856120757994353)
- [ ] [The pitfalls of A/B testing in social networks](https://tech.okcupid.com/the-pitfalls-of-a-b-testing-in-social-networks-17d631d7b20d)
- [ ] [How Meta tests products with strong network effects](https://medium.com/@AnalyticsAtMeta/how-meta-tests-products-with-strong-network-effects-96003a056c2c)
- [ ] [From Infrastructure to Culture: A/B Testing Challenges in Large Scale Social Networks ](dl.acm.org/doi/10.1145/2783258.2788602)
- [ ] [Sequential A/B Testing Keeps the World Streaming Netflix Part 1: Continuous Data](https://netflixtechblog.com/sequential-a-b-testing-keeps-the-world-streaming-netflix-part-1-continuous-data-cba6c7ed49df)

<a name="feed_ranking"></a>
# Feed Ranking


<a name="travel"></a>
# Travel
- [x] [Prioritizing Home Attributes Based on Guest Interest | AirBnB](https://medium.com/airbnb-engineering/prioritizing-home-attributes-based-on-guest-interest-3c49b827e51a)

      Personalize recommendation to hosts based on guest interests in unstructured data
      Attribute prioritization system -
      - collect text data from messages to hosts, comments in reviews, customer support requests.
        - for e.g. wifi, free parking, a private hot tub, or access to the beach
        - Parse data and retrieved entities
            - NER - Named entity recognition. Extract key phrases.
                Classify phrases into 5 categories(Amenity, Activity, Event, Specific POI, Generic POI) usign textCNN.
            - Entity mapping: Map phrases to home attributes
                Cosine similarity of key phrase with the word embedding of pre-labelled attributes.
      - build understanding of what home amenities, facilities, location features guests prefer.
        - Compute frequency of each entity and aggregate them over different text sources.
        - find most important entities and highlight the ones not supported yet.
      - Recommend hosts on what features to acquire, advertise and verify
        - Uniquely rank attributes for each home
          - Given characteristic of home such as property type, location, capacity, luxury level, predict the frequency of each attribute occuring in messages, reviews and requests.
          - Calculate customised importance score for each possible attribute, based on the above freqiencies.\
          - If the attribute is important and it exists or needs clarification, host can be sent recommendations.
- [x] [Expedia Group’s Customer Lifetime Value Prediction Model](https://medium.com/expedia-group-tech/expedia-groups-customer-lifetime-value-prediction-model-7927cdd44342)

      Customer lifetime value: Refers to future cash flow capabilities of a customer over long term periods.
      Problem statememt: Identify high lifetime value customers to plan aquisition and retention of customers.
      Exisiting non-ML techniques for CLV predictions -
            - Cohort analysis : Can be calculated only for predefined segmemts.
            - RFM (Recency, Frequency, Monetary) : Only past transactions are considered, but non-monetary like engagement and customer satisfaction are not considered.
            - Statistical buy-till-you-die : Can not be accurately used for new customers since multiple transactions for 1 user are needed.
      Solution
            Build a supervised learning model using gradient boosted trees that uses multiple input features capturing user past transactions and engagements.
      Data: Collected across companies and for different verticals like flights, stays, packages, cabs, etc and divided into -
            Booking
                  - detailed insights of recent purchases like brand, platform, value, region, etc.
                  - aggregated features for past transactions across levels like 3 months, 6 months, 12 months. Features being - total bookings, avg. gap between bookings, total booking value, avg booking window, proportions between different brands 
            Engagement: Customer interactions with the platforms other than just booking. Engagement with loyalty programs, marketing campaings, etc.
            Cut-off date : Engagements and purchases before cut-off date can be used to compute input features and data after that is used for predicting lifetime value.
      Modelling :
            CLV model - a collection of 30 different catboost models trained for differnt regions, recency, frequencies. Each segment has different features, that way unique needs of each of the region and groups are handled.
            CLV multipliers - Scale the gross CLV predictions from the model to net CLV to account for cancellations.
            Model Evaluation -
                  - Lorenz curve and gini coefficient : Model's differentiability of high CLV customers with rest
                  - RSME and bias : How far are the predicted values from actuals
                  - calibration plots : If the predictions are in the same scale as the actual values.
            Challenges : Feature computation optimization. Erratic behaviour during covid.
      MLOps : EG's unified platform to train, deploy, maintain features, maintain models versioning, monitor health
            - Model development is done in databricks notebooks.
            - GitHub is used for code maintainance and version controlling. Changes pushed to prod only after integration tests are finished.
            - Data source is s3 and acessed using Hive. Data pipelines are writtin in spark on kubernetes.
            - EG compute platform : Kubernetes based container on which models are trained and scored. Individual step is containarized. The platform supports ops like logging, metrics, scheduling, security, tracing.
            - Model repository service : To manage models and their versions
            - Airflow for workflow orchestration : Useful for batch inferencing using multiple models.
            - Machine learning workflows are deployed through pre configuerd CI/CD pipelines. CI/CD workflow implemented using Github actions, spinnaker and artifactory.
            - DataDog for infra monitoring. Alert mechanisms for training and scoring jobs, cluster health, job status, workload, logs investigation(splunk).
       
- [x] [Categorising Customer Feedback Using Unsupervised Learning](https://medium.com/expedia-group-tech/categorising-customer-feedback-using-unsupervised-learning-8608c1e62d48)

      Problem : Group customer feedback messages into categories to be routed to right teams.
      Solution : Multilabel classification using unsupervised learning
      Initial efforts
            Multilabel classification using supervised learning: Would require a lot of pretrained data.
            Multilabel classification using word synonym : Hard to capture the same context by mere context. Flight and plane are synonymous but flew is not.
      Current solution : Leverage pretrained word embedding models to understand context since it can better model the distance between the target words and keywords from the feedback messages. Word embeddings canplace words of the same context together like flight, flew, pilot, etc.
            Word2vec - shallow neural network is trained on word - word co-occurance
            GloVe Embeddings - pretrained GloVe embeddings
      Preprocess the text into keywords. Then retreive categories for keywords based on threshold on similarity with each category. This threshold is tuneable to each category.
            
- [ ] [Personalization in Practice](https://booking.ai/personalization-in-practice-2bb4bc680eb3)

      Personalization and recommendation are late adopters of novel solutions because of problem hardness. Trends explored - deep learning, causality, active exploration with bandits. Topics covered - explainabiity, fairness, content generation, natural interfaces.

      Deep Learning :
            Sequence in recommender systems:
            Image classification:
            Multi task learning
      Causality:
            Feedback loops : Actions results in effects. Use feedback loop to retrain models.
            uplift modelling :
            A/B testing :
      Active Exploration
            Contextual bandits
            REinforcement learning
            Human in the loop
      fairness and explainability
            Factorization methods for explainability
      Content Generation

      Multi task learning
            Bundling

      Sequence modelling : Multidestination trip, DEstination recommendation. Next destination prediction
            RNN to predict next destination, given a starting destination.
            GRU. LSTM to solve vanishing gradient problems.
            Context features in
                  seq level features : Does not change over time
                  token level features :
                  Important feature - days to next
      
- [ ] [Using Synthetic Search Data for Flights Price Forecasting](https://medium.com/expedia-group-tech/using-synthetic-search-data-for-flights-price-forecasting-4cf3277afdaf)

<a name="e_comm"></a>
# E-commerce
- [ ] [Evolving Recommendations: A Personalized User-Based Ranking Model](https://innovation.ebayinc.com/tech/engineering/evolving-recommendations-a-personalized-user-based-ranking-model/)

      - A deep learning based ranker for candidate recommendations for personalized recommendations.
      - In the past, item based contextual recommendations were popular but sometimes only user context is present like homepage, feed, personalized recommedation module based on user's shopping behaviour.
      - Personalized recommendation for user has 2 steps - candidate generation and ranker based on a business objective like CTR, purchase through rate.
      - A deep learning ranker on user's historical behaviour is used to predict user's click and purchase actions.
      - Model structure : A deep and wide architecture for the user based ranker.
            - Deep model like RNN to model user's sequential behaviour
            - Bottom layers sharing to perform multi-task learning
            - leverage user and recommended item embeddings from other pre-trained embedding models
            Deep Structure: Provides generalization capability
                  - Fully connected neural network taking input from transformed features.
                  - Concatenation of
                  - Numerial features : Relationship of candidate item with user's past history
                  - Embedding features : Projection of categorical features.
            Wide Structure: Provides memorization capability
                  - shallow network that will correct the weakening of user features casused by deep network.
                  - memorization is helpful for id related features like user_id, item_id, but might not be helpful when user and item patters vary a lot.
      - Feature engineering
            - User features determine upper bound on model performance
            - Pre-trained embedding features
                  - User and item features from a tewo-tower based personalized recall model which has learnt implicit represenation based on user's behaviour history and item information.
                  - feed the features directly to model since they are dense features
            - Derived features
                  - Effective features with more business explainability.
                  - Freshness features to measure user's decay of interest.
                  - User's intrinsic preferences and browsing behaviors captured via add-to-cart and transaction features.
      - Loss function
            - Pair-wise loss function to optimize for click and purchase probability at the same time.
            - In the case of ranking, the objective it to minimize incorrect ordering of recommended items, in comparision to relevence score or classification.
            - Pair-wise loss function comes up with optimal ordering of 2 items where preference of 1 item is learnt given another item.
            - $L_{loss} = log(1 + e^{-pairwiseTargetLoss*pairwiseModelScore})$
      - Offline Evaluation
            - NDCG : Normalized discounted cumulative gain
      
- [ ] 

      
- [ ] 

# Other resources
- [Chip Huyen's book](https://github.com/chiphuyen/machine-learning-systems-design/blob/master/content/case-studies.md)
- [Evidently Ai](https://www.evidentlyai.com/ml-system-design)
