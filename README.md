# News_Classification_and_Vectorization

This project implements: news gathering -> preprocessing -> vectorization -> classification

***Content:***
- [Data collection](#Data-collection)
- [Data preprocessing](#Data-preprocessing)
- [Vectorization](#Vectorization)
- [Classification](#Classification)



## Data collection <a name="Data-collection"></a>

[Parser_news_LENTA](https://github.com/andreytsimbalov/Diplom/blob/main/Parser_news_LENTA.ipynb) 
creates 12 datasets (one for each month of 2020) in the format **data/data_on_months/news_lenta_XX_2020**

Likewise: 
[RIA](https://github.com/andreytsimbalov/Diplom/blob/main/Parser_news_RIA.ipynb),
[RBC](https://github.com/andreytsimbalov/Diplom/blob/main/Parser_news_RBC.ipynb)

[data_news_corrector_2020](https://github.com/andreytsimbalov/Diplom/blob/main/data_news_corrector_2020.ipynb)
combines all collected data and normalizes their shape.
Only the *tags - dt - main_text - website* columns remain.
Final dataset **data/news_main_2020**



## Data preprocessing <a name="Data-preprocessing"></a>

[data_preprocessing](https://github.com/andreytsimbalov/Diplom/blob/main/data_preprocessing.ipynb)
conducts data preprocessing.
Stemming / lemmatization, removal of stop words, replacement of numbers with unified analogs are performed.

It also creates tags based on tags from websites for further classification:
 - economy
 - entertainment
 - traditions
 - science
 - society
 - sports
 - technology

Final dataset **data/news_main_prepr_2020**, as well as **data/data_stem & data/data_lemm**




# Vectorization <a name="Vectorization"></a>

[vector_model_creator](https://github.com/andreytsimbalov/Diplom/blob/main/vector_model_creator.ipynb)
performs vectorization:
 - **tfidf_lemm_500k** - tfidf
 - **d2v_300** - Doc2Vec
 - **ft_lemm_300** - FastText
 - **w2v_tfidf_vector_data** - Word2Vec
 - **glove_tfidf_vector_data** - GloVe
 - **use_vector_data** - Universal-sentence-encoder
 - **bert_vector_data** - Bert

all models are stored in the **models/** folder



# Classification <a name="Classification"></a>
[Classifier_news](https://github.com/andreytsimbalov/Diplom/blob/main/Classifier_news.ipynb)
makes a classification:
 - LogisticRegression
 - SVM
 - Single-layer perceptron
 - Bert
 - Gpt-2

for *LogisticRegression, SVM, Single-layer perceptron* models, preliminary vectorization is performed using one of the previously described methods.

