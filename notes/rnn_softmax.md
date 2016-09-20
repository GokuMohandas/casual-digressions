## [On Using Very Large Target Vocabulary for Neural Machine Translation] (http://arxiv.org/abs/1412.2007) - Sampled Softmax 

I wanted to mainly read Section 3 of this paper for the negative sampling softmax details.

TLDR; When computing the softmax of the output from our decoder, the denominator involves taking the sum of probabilities for all the words. This is not feasible for a large dataset. So we will use negative sampling. 

1.) We will only take a small subset V' from the entire vocab size V. We will also use a predefined proposal distribution Q. 

2.) We will define our subset V' by looking at each training subsequence input and collecting words into V' until a threshold amount is met. The proposal distribution is different for each training subsequence and if defined by each training subsequence's subset V'. 

![softmax] (images/rnn_softmax/softmax.png)
