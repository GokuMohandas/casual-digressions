## - [GRAM: Graph-based Attention Model for Healthcare Representation Learning] (https://arxiv.org/abs/1611.07012)

TLDR; Data insufficiency and interpretation are two common issues when using deep architectures. This is especially true for a lot different healthcare related tasks where these two issues cannot be overlooked. This paper introduces the GRaph-based Attention Model (GRAM) which uses an attention mechanisms to represent medical concepts.

### Detailed Notes:

- The objective of the models discussed in this paper is to take clinical event information from a patient's health record and predict the events that will occur in the next visit. These events could be a multiple of different things but one common attribute are the International Classification of Diseases (ICD) codes from each clinical visit. 

- Data insufficiency in terms on electronic health records (EHR) occurs in the form of limited data samples for a particular rare occurrence (disease, condition, etc.). Since we do not have enough data, it is hard to develop useful representations for these events to receive accurate predictions.

- Interpretability is the other issue, especially with health related tasks, because it is very important to know why predictions are as they are. It is important that the representations these deep models ultimately converge to are highly correlated with our medical understandings of those inputs. 

- The paper uses medical ontologies (hierarchies of medical information where one ICD code can be a parents and a children of other parent nodes) to encode the inputs. This incorporate of this medical ontology information helps the data insufficiency issue by reducing the number in input features needed to be assessed. So if you think of the model training as learning how to classify many different types of input combinations (say for a particular disease), if the disease does not have much data, this will be a difficult task. But by using the heirarchial information for the disease, we are able to retrieve more information abut the diseases and it's parents. These parents will be the parents of other diseases as well, which now gives us some more useful information to encode about our rare disease. 

- The GRAM method infuses the medical ontologies into the encoding process by using an attentional interface. I don't think I can say it better than the paper can for how they use this information to create representations: 

```bash
"Considering the frequency of a medical concept in the EHR data and its ancestors in the ontology, GRAM decides the representation of the medical concept by adaptively combining its ancestors via attention mechanism." 
```

The intuition is that when a medical event lacks enough data points, more weight is given to the ancestors of that event (parent nodes), since they can be learned better (since data exists for them via other child events). This effectively solves both the issue of data insufficiency and interpretation. 

#### Representations via GRAM:
- Now we will discuss the details of how the authors decided to embed each of the patients information.

![eq1](images/gram/eq1.png)
- The codes (ex. ICD codes) are all represented by a set C and the clinical records of each patient is represented by V (for T visits), where each visit V_t is composed of x_t which is a binary result for each code (wether or not is given for that clinical visit). 

![diagram1](images/gram/diagram1.png)
![eq1](images/gram/eq2.png)
![eq1](images/gram/eq3.png)
- Now we need a way of embedding the codes for each visit. A paper uses GRAM to incorporate the medical ontology information in the embedding procedure.

![eq1](images/gram/eq4.png)
- We take the embedding matrix G to embed the visit into V_t into v_t, which will be used in the end to end architecture. The embedding involves doing a matmul of G and each x_t and applying a tanh nonlinearity. Then for each v_t (which represents an embedded visit), we feed into an RNN whose output is used with a softmax operation. So the predicted y (yhat) has \mathcal{C} items where each item is the change of that code appearing for the next visit. We use this with a binomial cross-entropy loss (since ground truth is also \mathcal{C} items but with binary values). This is repeated for each t in V_T visits. (Ex. V1 used to predict V2, V1 + V2 used to predict V3, up to V1 + ... V_T-1 to predict V_T). 



### Training Points:

-


### Unique Points:

- 



