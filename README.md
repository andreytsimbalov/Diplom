# Diplom

Данный проект реализует: сборку новостей -> предобработку -> классификацию -> *разбиение на тематики*

***Содержание:***
- [Сбор данных](#Data-collection)
- [Подготовка репозитория](#Preparing-repo)
     - [Подготовка документации](#Preparing-doc)
     - [Оценка качества кода](#Codacy)
- [Подготовка автоматической сборки в Travis CI](#Travis-CI)
     - [Разработка сборочного скрипта setup.py](#Setup)
     - [Настройка конфигурации в .travis.yml](#Configuration)
     - [Подготовка и настройка репозитория в PyPI](#PyPI)
- [Публикация новости о релизе в Telegram-канале DevOpsHQ](#News)
- [Проверка тестового проекта](#Testing)


# Введение <a name="Introduction"></a>

## Сбор данных <a name="Data-collection"></a> Data collection

**Parser_news_LENTA** создаёт 12 датасетов(по одному на каждый месяц 2020 года) в формате **data/data_on_months/news_lenta_XX_2020**

Аналогично: **RIA, RBC**


**data_news_corrector_2020** объединяет все собранные данные и нормализует их форму. 
Остаются только *tags	- dt - main_text - website* столбцы.
Итоговый датасет **data/news_main_2020**

## Data preprocessing

**data_preprocessing** проводит предобработку данных.
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

# Vectorization

Данные векторизуются:
 - **tfidf_lemm_up** - tfidf с балансировкой классов вверд
 - **tfidf_lemm_down** - tfidf с балансировкой классов вниз
 - **d2v** - Doc2Vec
 - **w2v_lemm_300** - Word2Vec
 - **ft_lemm_300** - FastText

все модели хранятся в папке **models/**

