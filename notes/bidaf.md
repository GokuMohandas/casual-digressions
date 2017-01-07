## - [Bidirectional Attention Flow for Machine Comprehension](https://arxiv.org/abs/1611.01603)

TLDR; In order to accurately answer questions based on a document, we need to be able to model complex interactions between the document and query. This paper uses the Bi-Directional Attention Flow (Bi-DAF) network to process an attention context that is query aware, and represents the document at different levels of granularity. It's main advantage is the bidirectional attention flow, which eliminates the early summarization issue we see with normal uni-directional attentional interfaces. Furthermore, the BiDAF does not use just one context vector (summary) but uses vectors from all time steps (so no temporal coupling).  

### Detailed Notes:

#### Introduction

- The general BiDAF architecture follows the same pattern as those of competing QA structures (DMN+, DCN, etc.) They all use some form of an attentional interface in order to be able to focus on important parts of the input document with respect to the query. 

- BiDAF uses three different representations of the context at various levels of granularity (character-level, word-level, phrase-level embeddings). Which are then attended to by a bi-directional attentional interface to create a query-aware context representation. 

- Three pitfalls of traditional attentional interfaces:

![eq1](images/bidaf/eq1.png)

#### Model

- The model consists of six different layers:

![diagram1](images/bidaf/diagram1.png)

![eq2](images/bidaf/eq2.png)

- Now we will dive deeper into each of the six layers. 

- 1.) Character embedding layer: We want to map each word to a higher dimensional vector space. We can achieve this by using character level embeddings for each word using CNNs. The char-level CNN is taken from Yoon's 2015 paper on using CNNs for text classification and was also used in Facebook fully character level NMT model. 

- We will use my notes from the fully char model paper. Instead processing chars in the entire sentence (for NMT), we will process all chars in a particular word. 

![diagram1](images/bidaf/math1.png)
![diagram1](images/bidaf/math2.png)
![diagram1](images/bidaf/math3.png)

- First we will embed each character in our word into vectors which we will input into the CNN as a 1D input. The conv layer gives us an output which we apply max-pooling (using the same width as the word) to get a fixed sized vector for any word.

- 2.) Word embedding layer: this layer also maps each word to a higher dimensional vector spaces but uses the pre-trained GloVe vectors. 

### Training Points:

-


### Unique Points:

- An action packed reading; felt like I was in an action movie. 



