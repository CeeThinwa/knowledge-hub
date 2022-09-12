# ML/Data Science article 4

## Delivering Success in Natural Language Processing Projects: Part Two

**Publisher**: [*Medium*](https://medium.com/@ceethinwa/delivering-success-in-natural-language-processing-projects-part-four-405e8d5a407a) <br>
**Publishing Date**: *Sep 12, 2022*

*This is the fourth post of a five-part series where I aim to demystify Natural Language Processing (NLP) through a key learning tool that I would call the **NLP toolbox**. You can access the first article [here](https://medium.com/@ceethinwa/delivering-success-in-natural-language-processing-projects-part-one-40c4775cf6a9).*

What a ride! We got to explore both types of NLP data and visualize them in the previous section. Before we move any further, based on the last three parts, it’s clear to see that:

1. **Problem Identification** is a *process* of recognizing *valuable* problems that are *hard* for most people but *easy* to solve when *technology* and *creativity* are combined.
2. **Data Exploration** is a *process* of *analyzing* the data to find *patterns* within it and *summarize* key characteristics of the data.

----

### Feature Engineering

> So, what is Feature Engineering?

**Feature Engineering** is a *process* of *transforming* the data to make it *easier* for the computer to "understand" and produce *relevant* results during modelling.

It consists of various elements as shown:

![feature enginnering flowchart](../images/feature-enginnering.svg) <br>
*Feature Engineering visualized.*

Feature Engineering in NLP, as you can imagine, tends to be very difficult to understand and apply because

* data cleaning,
* domain knowledge,
* data pipelining,
* data validation and
* data relevance

are also broad. Furthermore, it is a repeated process because both

1. Concept drift — when the project goals change for the particular NLP project, and
2. Data drift — when the distribution of categories in NLP data changes

happen.

[Learn more about concept and data drift [here](https://medium.com/mlearning-ai/concept-drift-data-drift-and-machine-learning-monitoring-how-to-keep-your-model-accurate-66f3c91c7888).]

Due to the fact that feature engineering is cyclical, it should ideally be in the form of a data pipeline of some sort that is monitored, with model outputs identifying areas of improvement for the pipeline over time.

Depending on your NLP task and data type, feature engineering greatly varies.

<br>

#### **Data Cleaning**

##### **Data Cleaning for Audio**

As highlighted earlier, feature engineering audio typically tends to involve the data encoded in the form of spectrograms, ready for modelling.

Remember the visualizations below?

![left channel](../images/left.png) <br>
![right channel](../images/right.png)

These were spectrograms of [this audio](https://ceethinwa.github.io/resources/aud/Abstract.mp3). Based on the visualization, we get an important insight: The sound was mixed to be identical for both left and right channels. Assuming there are a couple of audio files, spectrograms for only the left channel could be selected for modelling and feature engineering would be complete.

> However, using only spectrograms would create hidden features, making resulting models **uninterpretable** and **unexplainable**.

An alternative to spectrograms is to transcribe the audio, converting it to text data. Each audio would be represented as text transcripts as well, split by particular timestamps. At the moment, transcripts in English can be easily generated, with humans speaking the language reviewing the file to ensure accuracy and meaning are kept. However, for many low-resource languages, accessing audio — let alone transcribed audio — is difficult.

It is recommended to have more than one form of encoded audio data e.g. representing the same data as both a metadata table and spectrogram, which can each have an ID label linking the two.

[*Librosa*](https://pypi.org/project/librosa/) is a popular Python package used to identify spectral and rhythm features from any audio represented.

##### **Data Cleaning for Text**

Cleaning text data involves encoding it and removing unnecessary symbols — exactly what was done during data exploration. Text data can be encoded in two ways:

* Manually and
* Programmatically.

If encoded manually, it can be encoded in such a way that key words or phrases are kept i.e. one-hot encoding. Findings from data exploration and available domain knowledge would inform feature selection. This would typical result in direct feature extraction (if original dataset was text) or a metadata table (if original dataset was audio).

A benefit of manual encoding is that it gives human oversight to model input and it facilitates interpretability. However, the data annotation process can be quite tedious, and it tends to be poorly-paid work, relative to other aspects of feature engineering, such as feature selection and pipeline building.

Programmatic encoding can be very helpful in identifying hidden features that a human being may not have typically thought of, and it involves use of unsupervised machine learning models. However, we run into the same problem of model interpretability.

Programmatic encoding models include:

* *TF-IDF* (Term frequency-inverse document frequency) model — learn more about it [here](https://www.geeksforgeeks.org/tf-idf-model-for-page-ranking/)
* *PV-DM* (Distributed Memory Model of Paragraph Vectors) model — learn more about it [here](https://cs.stanford.edu/~quocle/paragraph_vector.pdf); it is implemented in a Python package, [Gensim](https://pypi.org/project/gensim/)
* *PV-DBOW* (Distributed Bag of Words model of Paragraph Vectors) model — learn more about it in the same article describing PV-DM; it is also implemented in Gensim
* *LDA* (Latent Dirichlet Allocation) model — learn more about it [here](https://www.geeksforgeeks.org/latent-dirichlet-allocation/); it is implemented in a Python package, [pyLDAvis](https://pypi.org/project/pyLDAvis/)
* Use of *Transformers* (pre-trained and validated deep learning models) such as BERT; learn more about transformers in general [here](https://medium.com/inside-machine-learning/what-is-a-transformer-d07dd1fbec04)

Further data examining similarity between specific vectors can be used to evaluate the effectiveness of this type of unsupervised encoding as shown [here](https://medium.com/analytics-vidhya/best-nlp-algorithms-to-get-document-similarity-a5559244b23b) and [here](https://gab41.lab41.org/doc2vec-to-assess-semantic-similarity-in-source-code-667acb3e62d7).

<br>

#### **Domain Knowledge**

Before you feed hidden and opaque features into your model of choice, it is best to collect domain knowledge in the problem space that you are operating in. There are two kinds of domain knowledge needed to adequately perform feature engineering:

* **Technical domain knowledge**: This involves machine learning research done by computer scientists and general information available on the internet from data professionals on what ML techniques are best for audio files of different types. [This article](https://towardsdatascience.com/visualizing-audio-data-and-performing-feature-extraction-e1a489046000) seeks to demonstrate how to extract features relevant for music classification while [this article](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/FeatureEngineeringInCD-DNN-ASRU2011-pub.pdf) compares different feature engineering methods used in transcription.
* **Contextual domain knowledge**: This involves getting specific peculiarities of the culture the music and/or language is in, such as different accents, culturally-specific vocabulary, or typical instrumental arrangements (for music audios). This is typically provided by a Subject Matter Expert (SWE)— this could be a person who lives/works in the context that the audio was generated in (e.g. a doctor being a SWE for a hospital’s emergency response calls) or an academic studying the audio generated (e.g. a linguistics professor specialized in West African languages being a SWE for Ghanaian and Nigerian pidgin news audio). In the absence of a SWE, resources generated from and about the culture under study could give context.

>> One thing is clear — we need to have more than one type of encoded data, be it audio or text; the data has be be represented in manually encoded and programmatically encoded forms to account for both forms of domain knowledge.

<br>

#### **Data Pipelining**

Data pipelining involves all the activities that ensure data from multiple, relevant sources is ingested, cleaned and transformed in a systematic way. A good data pipeline consists of:

* **Documentation** of data sources, steps in data transformation and how various dataflows are orchestrated; this is helpful when down the road, the data pipeline needs to be maintained and the data engineer needs to understand the context of a particular transformation step. This can be as simple as keeping an Excel file or Jupyter notebook, or as complex as automated alerts operating in serverless environments.
* **Version control** of the code that makes up the pipeline itself, documentation and data storage; this keeps various copies of the data at each transformation step separated from each other (allowing for rollback to earlier versions), tracks changes to data input and output, and it prevents raw data from being converted into features by accident. It can be as simple as having 2 folders: raw and transformed connected by code and notes in a Jupyter notebook — or as complex as a series of event alerts from a PubSub service in a cloud environment, with backup done via git integration.
* **Scalable data storage** helps avoid the problems that come with underutilized or minimal storage and also accounts for rapid growth of data over time. Currently, the most scalable place for data storage is in a cloud environment, where you only pay for the server space that you use, and technologies have evolved from rigid SQL, to more flexible noSQL databases, to object stores (that can store complex data like images, audio and video), to data warehouses that contain a mix of the aforementioned technologies. As this is relatively new, it can be prohibitively expensive for an individual — hence most devices currently (computers, smartphones, watches) rely on relatively static storage.
* **Simplified, yet flexible data flows** — as data grows and the pipelines under maintenance increase, it is important to have a pipeline that can be adjusted based on the situation at hand. Many tech giants who rely on sophisticated data storage and data flow solutions, are under increased data regulation, even as their data increases exponentially — this has forced them to make sure that their data pipelines can be accessed by people with the relevant credentials for purposes of satisfying IT auditors and government regulators. Balancing simplicity with flexibility can be incredibly difficult, but both are indispensable.

Data pipelines can vary widely, depending on the task at hand, but if we can follow these 4 principles, it becomes easier to build NLP solutions that are solid, even as the data and environment change.

<br>

#### **Data Validation**
