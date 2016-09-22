## [Neural Turing Machines] (http://arxiv.org/abs/1410.5401)

TLDR; https://www.youtube.com/watch?v=_H0i0IhEO2g

Essentially an architecture with a controller (FNN, RNN, LSTM) that has read/write access to a memory in order to learn a particular task. The controller gets an input, can read/write to memory block and then output a result. 

When reading and writing to the memory matrix, introspective attention is used. Separate attention weights for reading, erasing and writing. All of this is end-to-end differentiable, so theoretically we can learn very complex tasks. 

![model] (images/ntm/model.png)


