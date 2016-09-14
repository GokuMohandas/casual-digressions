## [Learning Phrase Representations using RNN Encoder-Decoder for Statistical Machine Translation] (http://arxiv.org/abs/1406.1078)

TLDR; Similar to Sutskever's paper on neural translation. Encoding and decoding are separate RNNs. The encoder maps variable length input to fixed length vector, decoder takes fixed length vector and maps to variable length output. 

### Detailed Notes:

- The translation architecture involves use separate RNNs. One for encoding the input sequence and the other for decoding the output from the encoder into our target sequence. 

![architecture] (images/rnn_encode_decode/architecture.png)

- The encoder maps variable length input to fixed length vector, decoder takes fixed length vector and maps to variable length output. 

- In the decoder, we will use softmax weights to predict the next word of the target sequence. At the end we will take the multiplicative series of all the probabilities to get the probability of the entire target sequence.

![softmax] (images/rnn_encode_decode/softmax.png)
![multiply] (images/rnn_encode_decode/multiply.png)

- The objective is to maximize the log probability of the target sequence given the input sequence. 

![objective] (images/rnn_encode_decode/objective.png)

### Training Points:

- 100 hidden units per state

- 100 dimensional embeddings

- adadelta and SGD (momentum = 0.95, epsilon = 10^-6)



