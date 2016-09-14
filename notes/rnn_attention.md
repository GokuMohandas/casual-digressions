## [Neural Machine Translation by Jointly Learning to Align and Translate] (http://arxiv.org/abs/1409.0473) - Attention in RNNs

TLDR; Instead of feeding a fixed size embedded vector into the decoder, we will allow the decoder to soft attention to focus on different parts of the input. Here we use a bidrectional RNN as the encoder and allow the decoder to apply soft attention. 

### Detailed Notes:

- Encoding does not result in a fixed length vector but rather creates a sequence of vectors and a subset of these vectors are chosen adaptively while decoding for the output sequence. 
This allows our model to prevent storing all the information from a long sentence in to a fixed length vector. 

- Compared to the basic RNN models, out state and the output are not dependent on this context vector c. This context vector depends on a series of annotations (h1 ...h_i ... h_T), where each annotations focus on the entire input sequence with strong focus on the i-th word. The context vector is the weighted sum of these annotations. 

- The probability alpha or it's associated energy e is a function of annotation h_j and the hidden state s_i-1 in order to decide the next state and y_i. This is how the decode implements attention and decides which parts of the sentence to pay attention to. 

![attention] (images/rnn_attention/attention.png)

- The encoder will be a bidirectional RNN because we also want to like the annotation of each word to be a summary of the previous and the following words. The annotations of the forward and reverse paths in the BiRNN are concatenated to get h1, h2, ... h_T. 

### Training Points:

- vocab size restricted to 30,000 most frequent words, other words are replaced with <UNK>. No stemming or lowercasing involved. 

- Very detailed implementation at bottom of pdf (past references). 

### Unique Points:

- Attention is referred to as alignment in this paper. Soft and hard alignment.

- Attention helps accurately translate short and especially, long sentences really well. 



