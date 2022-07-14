(ds-proj)=
# Past data stories

## What do Amazon customers think of Alexa?

### Skills at work

* Data visualization


:::{admonition} Project Summary
:class: tip
<u>_**Context**_</u>

When Amazon customers purchase an Amazon Alexa, a voice controlled-assistant,
some of them may chose to leave a review and give the product a rating. The rating ranges from 1 star to 5 stars. A sample of 3,150 customer reviews
(data source [here](https://go.aws/2WkOfZp)) were selected for analysis.

<u>_**Problem**_</u>

Help Amazon solve the following challenges:
1. It's been discovered that all verified_reviews that are only say "love it" or are only one word are actually fake. Reviews like "great!" or "Love It!" need to be removed from the dataset.
2. We need to see the number of customers that left a review each day from the sample reviews that we do have
3. We need to see the number of reviews classified by rating
4. Can we anticipate sentiment of Amazon Alexa reviews given the data at hand?

<u>_**Solution**_</u>

1. Python code leveraging the Pandas library found reviews that had two whitespaces and removed them
2. A lot of the reviews in the sample dataset happened towards the tail end of July 2018
3. A lot of the reviews were 5-star reviews, indicating an overwhelming sense of positivity in the reviews
4. Yes we can, leveraging the CatBoost classifier, created by Yandex (which is now open source)

<u>_**Resources**_</u>

My project notebook can be found
[here](https://github.com/CeeThinwa/Python-Data-Science-Notebooks/blob/master/Amazon_Alexa_Challenge_Revised.ipynb)
:::

## Who is the perfect Marketing Researcher?

:::{admonition} Project Summary
:class: tip
<u>_**Context**_</u>

The goal of this research is to help job-seekers seeking to work in the niche area of marketing research to gain a clear
and current understanding of how they should package themselves to become attractive to the “global” employer. Research
was based on data obtained from [Indeed.com](http://indeed.com/) in January 2020.

<u>_**Research Conclusions**_</u>


<u>_**Resources**_</u>

The notebook can be found
[here](https://github.com/CeeThinwa/Python-Data-Science-Notebooks/blob/master/Amazon_Alexa_Challenge_Revised.ipynb)
and the report can be found
[here](https://drive.google.com/file/d/1UTNIz8CHg2-bXxo5Sb540aXk--q6ZEza/view?usp=sharing)

:::




1. [Supplementing data sources to estimate the welfare level of Kiva borrowers](kiva.ipynb)