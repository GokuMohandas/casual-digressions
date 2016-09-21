## [A Neural Conversational Model](http://arxiv.org/abs/1506.05869)

TLDR; Using seq-to-seq models, we are training to produce output sequences from input sequences. The objective is to hold a conversation that helps solve some end goal defined by the input sequences and the output sequences make sense. 


### Detailed Notes:
- Using an input sequence, we want to predict an appropriate output sequence using a seq-to-seq RNN model.

![model] (images/conversation/model.png)

- Greedy approach during inference is just feeding in the previous output as the new input, but less greedy is using beam search and then narrowing down based on product of all probabilities. 

### Training Points:

- Used closed domain IT troubleshooting help desk Q/A and an open domain movie script dataset. 

- Quite a bit of cleaning up for both datasets, and for the movie one each sentence appears twice, once as the input and once as the output for some other input. 

- Evaluation was done by human comparison for 200 questions on the response of this model and the popular rule-based CleverBot. 

### Unique Points:

- the Neural Conversational Model (NCM) performs significantly better than CB. 



