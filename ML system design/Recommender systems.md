# Recommender Systems

- When the user is interacting with large catalogue of items like, Products at Amazon, Movies at Netflix, songs at Spotify, etc. user usually doesn't
know what they are looking for hence some items are supposed to be recommended to them.
- The need arises because before internet we were used to interacting with limited number of items due to limitation of physical spaces. But with internet
space has become abundantly large and can accomodate exponentially large number of items.
- Long tail phennomenon

  <img src='img/long tail.png' width="300">
Less popular articles are not stored in the offline stores. After a threshold, the popualrity of the items decreases drastically.
- Types of recommendation
  - Editorial and hadn curated : Done by the staff
  - Simple aggregates : Top 10, recent uplodads, most popular
  - Tailored to individual users : Personalized
- Formal model
  - Utility function : $u: C \times S \rightarrow R$ Maps user and items to a rating also known as User Item Matrix
  - Utility matrix is sparse

Challenges
- Gathering known ratings from matrix
- Extrapolate unknown ratings from known ratings. Only high ratings are preferred
- Evaluating extrapolation methods

Gathering Ratings
- Explicit method
  - Scalability : Most people do not leave ratings.
- Implicit method
  - Learn ratings from implicit actions
  - Hard to learn low rating from implicit actions
- In practice a combination of explcit and implicit ratings are used

Extrapolating utilities
- Utility matrix is sparse
- Cold start problem

Approaches to build recommender systems
1. Content based recommender systems
    Recommend items to customer X simialr to item rated highly by customer X
    - Take all items the user likes
    - Build item profiles for these liked items which is the description of items
        - set of featues like author, title, metadata, set of friends, etc.
        - item profile can be treated as a vector.
        - Text: TFIDF
    - Infer the user profile from item profiles
      - Simple : Weighted average of item profiles
      - variant : Normalize weights using average rating of user
      - For e.g. boolean utility matrix
      - star ratings for movies, use ratings to get profile weights
    - Take the item profile and take the user profile and find the ratings by taking the cosine similarity between user and items.
    - For the user, get the rating for all items, and pick items with highest ratings.
    - Pros:
      - Non need for data from users
      - Recommed to users with unique tastes
      - Able to recommend new and unpopualr items
      - Is more explnabale
    - Cons:
      - Finding appropriate features is really hard
      - Overspecialization
        - No recommendation after user's profile
        - We might not have enough information on users
        - unable to exploit quality judgement of other users
      - Cold start
        - For new users
      
 2. Collaborative Filtering 

# Evaluation metrics
- NDCG :
    - CG : Cumulative Gain
      $$CG_p = \sum_{i=1}^{p} rel_i$$
    - DCG : Discounted Cumulated gain
      $$DCG_p = \sum_{i=1}^{p} \frac{rel_i}{log_2(i+1)}$$
    - NDCG : Normalized Discounter Cumulated Gain. Nirmalize DCG in the range of 0 to 1 for varu=ying length queries.
      $$NDCG_p = \frac{DCG_p}{IDCG_p}$$
      $$IDCG_p = DCG of ideal ordering of query results by human labellers.$$


# Comment Recommender to maximize engagement on video

Following is the response from gemini - 

Building a system to recommend one comment for maximum engagement on your short video platform involves several steps and considerations. Here's a breakdown:

**Data Collection:**
  1. Comment Features: Gather data on various comment features: likes, replies, shares, flags, reports, timestamps, user engagement history.
  2. Content Analysis: Analyze the comment content itself: sentiment, word count, relevance to the video, humor, sarcasm, etc.
  3. User Data: Look at user interactions: watch history, demographics, interaction with similar videos, engagement with past comments.

**Recommendation Algorithm:**
  1. Filtering: Eliminate spam, offensive, irrelevant comments using keyword filtering, language analysis, and user reports.
  2. Scoring: Develop a scoring system based on collected data. High engagement features like likes, replies, shares can increase the score.
  3. Personalization: Consider user interests and past engagement to personalize the recommendation. Users who like humorous comments might see a different pick than those who prefer in-depth discussions.
  4. Diversity: Prioritize diversity in recommendations to avoid showing similar comments repeatedly.
  5. A/B Testing: Regularly test different recommendation algorithms and scoring systems to identify the best approach for maximizing engagement.

**Additional Considerations:**
  1. Community Guidelines: Ensure the recommended comment aligns with your platform's community guidelines and promotes a positive experience.
  2. Transparency: Consider informing users how comments are recommended, fostering trust and understanding.
  3. Moderation: Maintain human moderation to handle complex situations and prevent biased recommendations.
  4. Ethical Concerns: Avoid manipulation or misleading tactics to maximize engagement.

**Tools and Resources:**
  - Natural Language Processing (NLP) libraries for sentiment analysis and content understanding.
  - Machine learning frameworks for building and training recommendation systems.
  - User behavior analytics platforms for collecting and analyzing user interaction data.
  - Remember, creating the perfect recommendation system requires ongoing optimization and adaptation based on your specific platform and user base.

Bonus Tip: Highlight the recommended comment visually to encourage engagement and user curiosity.
