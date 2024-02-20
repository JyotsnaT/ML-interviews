# Concepts
- NDCG :
    - CG : Cumulative Gain
      $$CG_p = \sum_{i=1}^{p} rel_i$$
    - DCG : Discounted Cumulated gain
      $$DCG_p = \sum_{i=1}^{p} \frac{rel_i}{log_2(i+1)}$$
    - NDCG : Normalized Discounter Cumulated Gain. Nirmalize DCG in the range of 0 to 1 for varu=ying length queries.
      $$NDCG_p = \frac{DCG_p}{IDCG_p}$$
      $$IDCG_p = DCG of ideal ordering of query results by human labellers.$$
      
