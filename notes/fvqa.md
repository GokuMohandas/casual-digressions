## - [FVQA: Fact based Visual Question Answering](https://arxiv.org/abs/1606.05433)

TLDR; Architecture that can use an image to answer questions that cover the scope beyond just the information presented in the image by using supporting knowledge. These facts are automatically found from large-scale structured knowledge bases (KB). 

### Detailed Notes:
- Current visual question-answering (VQA) models can answer question relating to image classification, object detection and recognition very well. However, questions beyond this scope do not produce good answers. This is largely due to that fact that the only information available comes from the images. A nice example is being able to ask 'How many giraffes are in an image?' and the answer being based off of without really knowing anything about giraffes. 

- Most of the question that can be answered with just the image include physical attribute based questions such as color, number and physical location. This limitation does not allow us to classify the model as "AI-complete". If we were to look at an image and a question was asked, we would reason about the objects in the image but also use prior knowledge about those objects to properly answer the question. 

- This paper developed a dataset and model that uses structured knowledge bases to gather supporting information for a given image. Together, with information from the image and the supporting fact, we can answer a wide variety of questions. The paper considered all questions that can answered only with an external source of information.

- Theoretically, we could answer questions beyond the visual scope if we have a very large number of images that corresponds to every single important word in a query. This would be a very difficult endeavor and we would be reinventing the wheel here since we already have sources for facts.

#### Structure of the Supporting Fact
- The supporting facts need to be structured in order for any model to be able to make use of them. The facts from the paper come from existing knowledge bases and the form is a triplet from a large interlinked graph (arg1, rel, arg2), which signifies the relationship between two arguments. The information in our KBs can be easily processed using a query language. The authors used SPARQL to query the RDBMS. 

- Here are a few examples of the triplets:
![diagram1](images/fvqa/diagram1.png)

- Having triplets allows us to represent mutual relationships between objects/concepts. This creates an opportunity for the model to make stronger representations since we are factoring in the structural representation. I would take this even one step further, and for the concepts that do not have as much information, we can create a hierarchical fall back as well (GRAM).

- All the questions in the dataset can only be answered with both the image and some commonsense knowledge. A custom dataset was created by allowing users to choose images, visual concepts in the image and supporting fact(s). 

#### Image and Visual Concepts
- The information we extract from the image itself is very important since we need it to actually extract valuable supporting facts from a knowledge base. Fast-RCNN and similar models are used as object detectors, scene classifiers and attribute (action) classifiers.

- An example for an image is as follows:
![diagram2](images/fvqa/diagram2.png)


#### Knowledge Bases
- KBs are usually constructed by manual annotation (DBpedia, Wikipedia, etc.) or automatically extracted from unstructured/semi-structured data (WebChild, ConceptNet, etc.). The paper uses DBpedia, Webchild and ConceptNet.

#### Question Collection

#### Training



### Training Points:

-


### Unique Points:

- 



