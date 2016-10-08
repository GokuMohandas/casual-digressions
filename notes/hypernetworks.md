## [HyperNetworks] (https://arxiv.org/abs/1609.09106)

TLDR; The approach of using a smaller network (the hypernetwork (HN)) to generate weights for a larger network (main network). This will offer a feasible alternative to weight sharing because the HN will generate non-shared weights while requiring a just a few additional learnable parameters.

### Detailed Notes:

- The main network behaves normally (take some inputs and map to desired targets). However, the HN will take some inputs that contains information about the structure of the weights and create the weights accordingly for a specific layer.

![diagram1](images/HN/diagram1.png)

- An obvious advantage is the ability for the HN to generate dynamic embeddings vectors. So now the weights of the RNN can change dynamically with time step and depending on the input sequence.

![diagram2](images/HN/diagram2.png)

- Static HN for CNN:

![cnn](images/HN/cnn.png)

- The objective is to generate the kernel (filter weights) for each conv layer using fewer learnable parameters. For a traditional CNN, going from one conv layer to another will require a kernel of size (N_in f_size X N_out f_size) but by using a HN we can create kernels with the same dimensions but by using much less parameters. 

![cnn2](images/HN/cnn2.png)

- The static HN (2 layer NN) has it's own set of weights that will take in an embedded input z (unique for each conv layer) and will generate our kernel. The HN weights and z are learnable parameters and the HN weights are fixed for all conv layers. So now we can still have unique kernels for each conv but by using the same HN weights to generate each one based on the input z. This allows us to do a bit more weight sharing but much less parameter expense. 

- Also, if N_in != N_out, as is the case with practical image processing in the conv layers, we will have to do a little trick. We will have to concatenate smaller kernels in order to create the non-square kernel that we need.

- Dynamic HN for RNN:

- HyperLSTM:


### Training Points:

- HN play well with batchnorm and layernorm. 



### Unique Points:

- Non-shared weights for an LSTM generate by the HN performed better than the standard LSTM rnn model.



