## - [Highway Networks] (https://arxiv.org/abs/1505.00387)

TLDR; We need deep networks for better results but also for computational and statistical efficiency. But they are difficult to train/optimize, so we should highway networks which use a learned gating mechanism for regulating information flow.

### Detailed Notes:
- Depth of neural networks is crucial for learning intricate patterns but training/optimization becomes difficult with increasing depth. Highway networks allow us to regular flow of information through the network.

![eq1](images/highway/eq1.png)

- T is the transform gate (how much of the transformed information do we take to the next layer) and C is the carry gate (how much of the original input do we carry into next layer).

- Optimization of highway networks is almost independent of depth. The above shows us that the highway layer can smoothly vary between a plain affine layer and a layer that just lets its inputs through. Obviously, since T is sigma, which is bounded to (0,1), we would never face either of these extremes but instead we will have a balance between them.

### Training Points:

- The bias vector in the transform gates can be initialized with negative values. This means that the network is initially biased towards the carry gate (C). This was found to help bridge long-term temporal dependencies early in learning.

![eq2](images/highway/eq2.png)

- Highway networks converge significantly faster than plain networks.

![eq3](images/highway/eq3.png)

### Unique Points:

- Very similar to the information flow control in LSTM gates. Now we just apply it to any network layers for efficient training/optimization.



