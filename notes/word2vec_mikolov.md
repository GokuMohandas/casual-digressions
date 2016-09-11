## [Distributed Representations of Words and Phrases and their Compositionality](https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf)

TLDR; We can represent words as one hot encoded vectors but these hold none of the semantic relationships. Instead, we can embed the words with a high dimensional fixed length vector. These help us map the linguistic relationships of the words with other words. We can get these embeddings but using the CBOW (predict target word from context word) or skip-gram (predict context words from target word). Once the training converges, we can use the embeddings on a variety of NLP tasks. 

### Detailed Notes:

- Skip-gram model is about predicting context words from a target word. 

![Skipgram objective] (images/word2vec/skipgram.png)

- The objective of the skipgram model is:

![Skipgram objective] (images/word2vec/skipgram_eq.png)

where:

![Skipgram objective] (images/word2vec/skipgram_eq2.png)

 - As you can see, the softmax formulation is not feasible because the cost of computing the denominator is proportional to W. A solution is noise contrastive estimation (NCE) but a simple approach is negative sampling which is just using a small subset sample for the denominator. 

- Tp decide how to subsample, we use the probability discard formula below. t is usually 10^-5. and f is the frequency of the word. Frequency is occurances of word / all occurances of every word, so a high frequency word will have a high value P, which is the discard probability. (discard from subsampling). We dont want to subsample the high frequency words because their embeddings don't change much because they are always used with almost every word. 

![Subsampling] (images/word2vec/subsampling.png)


### Training Points:

- For small training datasets, negative sampling size will be 5-20 tokens and for large datasets, just 2-5 tokens is good enough. Difference between negative sampling and NCE is "NCE needs both samples and the numerical probabilities of the noise distribution, while Negative sampling uses only samples".

### Unique Points:

- To deal with phrases like 'New York' which are two separate words, we can use the formula below to identify the phrase words. If the score is above a threshold, the two words form a phrase (bigram). We can do 2-4 passes on the data which allows us to form even longer phrases. 

![Phrase] (images/word2vec/phrase.png)

