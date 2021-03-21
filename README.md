# Diplom

Данный проект реализует: сборку новостей -> предобработку -> классификацию -> *разбиение на тематики*

***Содержание:***
- [Сбор данных](#Data-collection)
- [Предобработка данных](#Data-preprocessing)
- [Векторизация](#Vectorization)
- [Классификация](#Classification)
- [Тематический анализ](#Еhematic-analysis)



## Сбор данных <a name="Data-collection"></a>

[Parser_news_LENTA](https://github.com/andreytsimbalov/Diplom/blob/main/Parser_news_LENTA.ipynb) 
создаёт 12 датасетов(по одному на каждый месяц 2020 года) в формате **data/data_on_months/news_lenta_XX_2020**

Аналогично: 
[RIA](https://github.com/andreytsimbalov/Diplom/blob/main/Parser_news_RIA.ipynb),
[RBC](https://github.com/andreytsimbalov/Diplom/blob/main/Parser_news_RBC.ipynb)

[data_news_corrector_2020](https://github.com/andreytsimbalov/Diplom/blob/main/data_news_corrector_2020.ipynb)
объединяет все собранные данные и нормализует их форму. 
Остаются только *tags	- dt - main_text - website* столбцы.
Итоговый датасет **data/news_main_2020**



## Предобработка данных <a name="Data-preprocessing"></a>

[data_preprocessing](https://github.com/andreytsimbalov/Diplom/blob/main/data_preprocessing.ipynb)
проводит предобработку данных.
Происводится стемминг/лемматизация, удаление стоп-слов, замена чисел на унифицированные аналоги.

Также создаются метки на основе тегов с вебсайтов для дальнейшей классификации:
 - economy
 - entertainment
 - other
 - science
 - society
 - sports
 - technology

Итоговый датасет **data/news_main_prepr_2020**, а также **data/data_stem & data/data_lemm**




# Векторизация <a name="Vectorization"></a>

[vector_model_creator](https://github.com/andreytsimbalov/Diplom/blob/main/vector_model_creator.ipynb)
производит векторизацию:
 - **tfidf_lemm_up** - tfidf с балансировкой классов вверд
 - **tfidf_lemm_down** - tfidf с балансировкой классов вниз
 - **d2v** - Doc2Vec
 - **w2v_lemm_300** - Word2Vec
 - **ft_lemm_300** - FastText

все модели хранятся в папке **models/**



# Классификация <a name="Classification"></a>


# Тематический анализ <a name="Еhematic-analysis"></a>

