## [Deep Neural Networks for YouTube Recommendations ](https://research.google.com/pubs/pub45530.html)

TLDR; 

#### Key Points:

- 
-

#### Notes:

-
-


#### Unique Points:

- Offline measures such as precision, recall, ranking loss, etc. provide very different results compared to live metrics such as A/B testing. 





Classic two-stage information retrieval dichotomy: deep candidate generation model and then a separate deep ranking model.

Videos corpus --> candidate videos generation --> rank the videos --> display recommendations

candidate generation: input is user's activity history and output is a small subset (100s) of videos from a large corpus. 
The candidate generation step provides broad personalization via collaborative filtering. Some of the features to compare with others users are videos watched, search queries, and demographics. 


Recommendation as Classification:
We need to predict that a specific video will be watches at time t among millions of videos i (classes) from a corpus V based on user U and context C. This is a simple softmax where we compare the score for video i with the sum of scores for all the other videos. The inputs for video i and user are embeddings. We also use negative sampling because computation of the softmax denominator is not feasible at this scale. 

![Softmax](images/youtube_softmax.png)




