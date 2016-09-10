<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## [Deep Neural Networks for YouTube Recommendations ](https://research.google.com/pubs/pub45530.html)

TLDR; 

#### Key Points:

- 
-

#### Notes:

-
-





Classic two-stage information retrieval dichotomy: deep candidate generation model and then a separate deep ranking model.

Videos corpus --> candidate videos generation --> rank the videos --> display recommendations

candidate generation: input is user's activity history and output is a small subset (100s) of videos from a large corpus. 
The candidate generation step provides broad personalization via collaborative filtering. Some of the features to compare with others users are videos watched, search queries, and demographics. 

Offline measures such as precision, recall, ranking loss, etc. provide very different results compared to live metrics such as A/B testing. 

Recommendation as Classification:
We need to predict that a specific video will be watches at time t among millions of videos i (classes) from a corpus V based on user U and context C. 

$X^2$



