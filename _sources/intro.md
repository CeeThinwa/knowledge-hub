# Hello 👋

Welcome to my knowledge hub!

It contains
* past articles around machine learning and data science and
* reviews of helpful resources and learning frameworks

The goal of this knowledge hub is to share what I have learned and
empower people to *create impactful research for mixed audiences*.

Click on any of the images to pick an area of exploration:

|   [![Computer Vision](./images/computer-vision.svg)](cv)   | [![Natural Language Processing](./images/NLP-chatbot.svg)](NLP) |
|:----------------------------------------------------------:|:---------------------------------------------------------------:|
|                     👆 Computer Vision                     |                 👆 Natural Language Processing                  |
| [![Data Storytelling](./images/data-storytelling.svg)](ds) |     [![Data Pipelining](./images/data-pipelining.svg)](dp)      |
|                    👆 Data Storytelling                    |                       👆 Data Pipelining                        |


Below is an excerpt from [an article I wrote](https://medium.com/@ceethinwa/delivering-success-in-natural-language-processing-projects-part-one-40c4775cf6a9):

<u>_**What is AI?**_</u>

*Artificial Intelligence, simply put, is the quest to make machines achieve general intelligence, where these machines can*
1. *receive data in varying size and complexity,*
2. *process it into generalized information, and*
3. *use this information to create ideas and act without human assistance.*

<u>_**What is ML?**_</u>

*Machine learning is a subset of artificial intelligence that focuses on the processing of data into information.*
*There are two ways that machine learning produces information:*
1. *A human creates a pattern and the model evaluates how well the data fits to the pattern based on statistical inference, and*
2. *The model creates the pattern and the model and human evaluate how well the data fits into the pattern*

_**Approach 1: Bayesian/Frequentist Statistical Modelling**_

*These types of models can have*
* *static estimated parameters when using an unchanging fixed dataset, or*
* *dynamic estimated parameters.*

*For models with dynamic estimated parameters, an objective/loss function is used that minimizes the error in the model. In this case the variables/features stay fixed, but the observations/instances change over time, altering the data distribution in the process.*

*These types of machine learning models can be great in that they can be interpreted by people. However, they do not do well on unstructured data and may be limited by the researcher’s choice of variables and research objectives — they have to attempt different variable combinations to get statistically valid results that also satisfy research objectives.*

_**Approach 2: Deep Learning**_

*These types of models have only dynamic estimated parameters, in part, because the model itself selects variables (inputs into a paticular neuron), and also experiments with different combinations of these variables to get optimal estimated parameters.*

*The only key criteria that the human can control are the hyper-parameters that include the*
1. <u>*activation function*</u> — *gives the first set of estimated parameters which are usually normalized and it tends to be non-linear,*
2. <u>*loss function,*</u>
3. <u>*model selection metric*</u> — *i.e. we say that the model has succeeded in its task and it can stop training when a certain threshold of the model selection metric is used,*
4. <u>*desired dimensions of the output*</u>
5. <u>*number of epochs*</u> — *the number of times the model will go over the data in order to identify the patterns.*

*A great benefit of this approach is that this model type is able to handle large amounts of unstructured data very well. However, because the variables and the parameter estimation method is unknown, interpreting how it obtained its results becomes very challenging.*

_**Natural Language Processing is an application of Deep Learning, alongside Computer Vision — think of Computer Vision as the “eyes” of the computer and Natural Language Processing as the “ears and mouth” of the computer. Both applications specialize in unstructured data, which is increasing in size as more and more people communicate on many digital channels today.**_
