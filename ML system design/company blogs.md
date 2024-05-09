# ML Case studies from industry

# AB test
- [ ] [Measurement and analysis of ranking at Instagram](https://www.facebook.com/watch/?v=1856120757994353)
- [ ] [The pitfalls of A/B testing in social networks](https://tech.okcupid.com/the-pitfalls-of-a-b-testing-in-social-networks-17d631d7b20d)
- [ ] [How Meta tests products with strong network effects](https://medium.com/@AnalyticsAtMeta/how-meta-tests-products-with-strong-network-effects-96003a056c2c)
- [ ] [From Infrastructure to Culture: A/B Testing Challenges in Large Scale Social Networks ](dl.acm.org/doi/10.1145/2783258.2788602)
- [ ] [Sequential A/B Testing Keeps the World Streaming Netflix Part 1: Continuous Data](https://netflixtechblog.com/sequential-a-b-testing-keeps-the-world-streaming-netflix-part-1-continuous-data-cba6c7ed49df)
# Feed Ranking



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
            
- [ ] 
# Other resources
- [Chip Huyen's book](https://github.com/chiphuyen/machine-learning-systems-design/blob/master/content/case-studies.md)
- [Evidently Ai](https://www.evidentlyai.com/ml-system-design)
