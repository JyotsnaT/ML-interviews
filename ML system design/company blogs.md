# ML Case studies from industry

# AB test
- [ ] [Measurement and analysis of ranking at Instagram](https://www.facebook.com/watch/?v=1856120757994353)
- [ ] [The pitfalls of A/B testing in social networks](https://tech.okcupid.com/the-pitfalls-of-a-b-testing-in-social-networks-17d631d7b20d)
- [ ] [How Meta tests products with strong network effects](https://medium.com/@AnalyticsAtMeta/how-meta-tests-products-with-strong-network-effects-96003a056c2c)
- [ ] [From Infrastructure to Culture: A/B Testing Challenges in Large Scale Social Networks ](dl.acm.org/doi/10.1145/2783258.2788602)
- [ ] [Sequential A/B Testing Keeps the World Streaming Netflix Part 1: Continuous Data](https://netflixtechblog.com/sequential-a-b-testing-keeps-the-world-streaming-netflix-part-1-continuous-data-cba6c7ed49df)
# Feed Ranking


# Travel
- [ ] [Prioritizing Home Attributes Based on Guest Interest | AirBnB](https://medium.com/airbnb-engineering/prioritizing-home-attributes-based-on-guest-interest-3c49b827e51a)

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
- [ ] 
# Other resources
- [Chip Huyen's book](https://github.com/chiphuyen/machine-learning-systems-design/blob/master/content/case-studies.md)
- [Evidently Ai](https://www.evidentlyai.com/ml-system-design)
