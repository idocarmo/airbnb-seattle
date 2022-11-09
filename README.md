# airbnb-seattle

**airbnb-seattle** contains a brief study of Airbnb Seattle data developed for Udacity's Data Science nanodegree program.

The analysis output and outcomes is discussed in the medium article available at [link](https://google.com)

## Source code
You can clone this repository in your machine with the command:

    git clone https://github.com/idocarmo/airbnb-seattle.git

## Project Setup
### Dependencies

airbnb-seattle project requires:
~~~~~~~~~~~~
  - python=3.8
  - numpy
  - pandas
  - matplotlib
  - seaborn
  - nltk
  - spacy
  - gensim
  - pyldavis
  - wordcloud
~~~~~~~~~~~~

### Environment
You can prepare the pyhton environment  with all the dependencies using ``pip``:

    pip install -U src/requirements.txt

or with ``conda``:

    conda env create -f src/environment.yml

## Repository Content


> 📂 [data](https://github.com/idocarmo/airbnb-seattle/tree/main/data) contains the Airbnb Seattle data files used in the analysis;\
> 📂 [report](https://github.com/idocarmo/airbnb-seattle/tree/main/report) contains analysis outputs;\
>📂 [src](https://github.com/idocarmo/airbnb-seattle/tree/main/src) contains the files for building the python environment;\
>📄 [icc-airbnb-seattle-exploring.ipynb](https://github.com/idocarmo/airbnb-seattle/blob/main/icc-airbnb-seattle-exploring.ipynb) is the Jupyter notebook that contains the developed analysis.  

## Analysis Steps

The main idea of the analysis was to understand what are the main characteristics that define a Airbnb superhost.

Having the business problem in hands and following the CRISP-DM steps, we started taking a look at the available datasets, the meaning of their fields and their data types.

After this first look we tried to address the following questions:
* How many superhost locations are in Seattle? What is its fraction in the universe of locations?
* Is superhosts' cancellation policy more flexible?
* Are superhosts for they care with cleaning?
* What insights on the superhosts review comments could offer us? 

The last question, in specific, is answered using NLP techniques. We fetched all the superhosts review comments and established a NLP pipeline where, comment by comment we 

~~~~~~~~~~~~~~
 - Stripped special characters and extra spaces;
 - Tokenized the text;
 - Lemmatized the tokens;
 - Removed stop words. 
~~~~~~~~~~~~~~

After this step we were able to create bi-grams from the processed reviews and create a word cloud. Why bi-grams? Because we intended to highlight the main characteristics of a superhost location, and a word cloud of the terms that appear the most in a sequence give us a better understanding of the context the words are in. We have also transformed the processed corpus with TF-IDF [[1]](#1), to give the words weights that considers not only their counting in the document but also their  in the corpus as a whole. 

Another approach to get insights from comments reviews was they topic modelling. For this we have used gemsin library to create a bag of words of the processed corpus and created a Latent Dirichlet Model (LDA) [[2]](#2) with the heuristic number of 5 topics. Finally we were able to visualize the LDA model output using pyLDAvis Python library [[3]](#3).

## References

<a id="1">[1]</a> 
Gensim TF-IDF model: https://radimrehurek.com/gensim/models/tfidfmodel.html

<a id="2">[2]</a> 
Gensim Latent Dirichlet Allocation: https://radimrehurek.com/gensim/models/ldamodel.html

<a id="3">[3]</a> 
pyLDAvis: https://pyldavis.readthedocs.io/en/latest/readme.html#usage
