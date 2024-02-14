# Recommender Systems

- When the user is interacting with large catalogue of items like, Products at Amazon, Movies at Netflix, songs at Spotify, etc. user usually doesn't
know what they are looking for hence some items are supposed to be recommended to them.
- The need arises because before internet we were used to interacting with limited number of items due to limitation of physical spaces. But with internet
space has become abundantly large and can accomodate exponentially large number of items.
- Long tail phennomenon

  <img src="ML system design/long tail.png" width="300">
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
