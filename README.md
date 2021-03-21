# Diplom

Данный проект реализует: сборку новостей -> предобработку -> классификацию -> *разбиение на тематики*

## Data collection
**Parser_news_LENTA** создаёт 12 датасетов(по одному на каждый месяц 2020 года) в формате **data/data_on_months/news_lenta_XX_2020**

Аналогично: **RIA, RBC**


**data_news_corrector_2020** объединяет все собранные данные и нормализует их форму. 
Остаются только **tags	- dt - main_text - website** столбцы.
Итоговый датасет **data/news_main_2020**

## Data preprocessing


