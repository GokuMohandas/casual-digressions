## Neural Machine Translation by Jointly Learning to Align and Translate] (http://arxiv.org/abs/1409.0473) - Attention in RNNs

TLDR; Instead of feeding a fixed size embedded vector into the decoder, we will allow the decoder to soft attention to focus on different parts of the input. Here we use a bidrectional RNN as the encoder and allow the decoder to apply soft attention. 

### Detailed Notes:

- Encoding does not result in a fixed length vector but rather creates a sequence of vectors and a subset of these vectors are chosen adaptively while decoding for the output sequence. 
This allows our model to prevent storing all the information from a long sentence in to a fixed length vector. 

![context] (images/rnn_attention/context.png)

- Compared to the basic RNN models, out state and the output are not dependent on this context vector c. This context vector depends on a series of annotations (h1 ...h_i ... h_T), where each annotations focus on the entire input sequence with strong focus on the i-th word. The context vector is the weighted sum of these annotations. 

![context] (images/rnn_attention/context2.png)

The probability alpha or it's associated energy e is a function of annotation h_j and the hidden state s_i-1 in order to decide the next state and y_i. This is how the decode implements attention and decides which parts of the sentence to pay attention to. 

### Training Points:

- 


### Unique Points:

- 



