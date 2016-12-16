## - [Quasi-Recurrent Neural Networks] (https://arxiv.org/abs/1611.01576)

TLDR; 
RNN's have limited parallelism because we have to feed in one time-step at a time since output depends on previous output. CNN's can be highly parallelized since the filter can be applied simultaneous across the sample but lack ability to store concepts such as memory/history. Quasi RNNs strike a balance between RNNs and CNNs and proved to offer better performance than LSTMs while also offering increased parallelism.

### Detailed Notes:
- RNNs, including gated versions (LSTMs/GRUs), cannot be parallelized since subsequent time step outputs depend on the previous output. Also as sequences get longer, all types of RNNs have trouble dealing with adequately holding pertinent information involving these long sequences.

- With CNNs, we can apply time-invariant filters in parallel across the entire input sequence. This also better scales for long sequences as we can change the filter sizes. CNNs, however, has no concept of memory and assume time invariance and cannot really make sense of large-scale sequence order information.

- A common solution was a hybrid model, such as the one from the [fully-character](fully_char.md) level NMT model, which used a CNN to process the char level input (long sequence) and then used pooling to reduce the dimensions but still preserve pertinent information. Then the RNN structure will use the reduced features as inputs. But the model for the fully char NMT cannot be parallelized because it still uses regular RNN structure.

![dim](dim.png)

#### Model:

![cnn](fig1.png)

- This paper employs the quasi-recurrent neural network (QRNN) for neural sequence modeling. QRNNs will allow us to parallelize across time-step and minibatch dimensions. 

![cnn](cnn1.png)

- When we apply our filters of width k on our input X to create our candidate vectors z, we do not want the filters to account for future inputs when making each z. In other words, each z_t depends only on x_{t-k+1} through x_t. This is known as masked convolution (van den Oord et al. 2016) and we implement this by simply padding the input to the left by k-1. Let's see what this looks like for a small input and k=2.

![cnn](cnn2.png)

- Our candidate vectors z are passed through a tanh nonlinearity. Now we have to use additional conv filters to obtain sequences of vectors for the elementwise (bc gates use elementwise sigmoid operations) gates required for our pooling function. If the pooling includes a forget gate and output gate, then our conv/pool operations can be summarized to the following.

![cnn](cnn3.png)

- You can see how when k=2, the masked conv operations appear very LSTM-like. When we use convolutional filters with large width (k), we are essentially computing higher n-grams features at each timestep, this is especially important for tasks such as character-level tasks since we need to capture long windows. 

- We can extend our pooling functions using different combination of gates. The paper explores the three variants below:

![cnn](cnn4.png)

#### Regularization:

- The paper extends zoneout (Kreuget et al. 2016), which modifies our pooling function to keep the previous pooling state for a subset of channels. This is equivalent to the following forget gate. On top of this, normal dropout is also applied between layers including the layer between embedding and first QRNN layer.

- Paper also extends skip-connections between EVERY QRNN layer which is known as dense convolution. This really improves gradient flow and convergence but now we have quadratic number of layers (L(L-1)). 

#### Encoder-Deocder:

![cnn](fig2.png)

- We use a QRNN encoder and a modified WRNN (with attention) decoder. The reason for a modified QRNN is that feeding in the last encoder hidden state (output of encoder's pooling layer) into the decoder's recurrent pooling layer, will not allow the encoder state to affect any of the gates in the decoder pooling layer. So the proposed solution is to use the final encoder hidden state with the outputs each decoder's output from its conv operations  (basically the last encoder hidden state from encoder pool operations is taken into account with the decoder's conv operations and both are used to determine the decoder's pool outputs). 

![cnn](forget.png)

- So now the modified operations in the decoder look like this:

![cnn](decoder.png)

- We also use soft attention, where the attentional sum is based on the encoder's last layers's hidden states. These are used with the decoder's last layer's un-gated hidden states via dot product and then normalized with a softmax.  

![cnn](attention.png)

### Training Points:

- QRNN out performed LSTMs with the same hidden size on language modeling, sentiment classification and character-level machine translation.

- The parallelism allowed for a 16X speed up for train and test times.


### Unique Points:

- I feel like Socher et al. at Salesforce are just churning out paper after paper. The models are quickly building in complexity but are also offering amazing results. 
