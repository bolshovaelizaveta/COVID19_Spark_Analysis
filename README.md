![Hadoop](https://img.shields.io/badge/Hadoop-3.3.6-orange?logo=apachehadoop&logoColor=white)
![Spark](https://img.shields.io/badge/Spark-3.5.1-FF9200?logo=apachespark&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.10.12-3776AB?logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-11.0.27-ED8B00?logo=openjdk&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-3.5.1-FF9200?logo=apachespark&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.3.0-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10.3-11557c?logo=matplotlib&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13.2-30A8D9?logo=seaborn&logoColor=white)

# Проект: Разработка системы анализа медицинских изображений для эпидемиологического мониторинга COVID-19

## Обзор проекта

Данный проект разработан как итоговая работа по дисциплине **"Базы данных для компьютерного зрения"**. Его основная цель — разработать комплексную аналитическую платформу для **эпидемиологического мониторинга COVID-19**, используя метаданные рентгеновских снимков. Проект демонстрирует практическое применение знаний о **распределенных файловых системах (HDFS), фреймворках для обработки больших данных (Apache Spark, PySpark, Spark SQL, Spark MLlib)**, а также навыков **ETL-обработки, SQL-аналитики, машинного обучения и визуализации данных**.

Цель проекта — применить на практике знания о **HDFS, Spark, PySpark** и базовых методах **машинного обучения** для решения реальной задачи анализа медицинских данных.

## Используемые технологии

* **Apache Hadoop (HDFS):** Распределенная файловая система для надежного и масштабируемого хранения больших объемов медицинских изображений и метаданных.

* **Apache Spark:** Мощная унифицированная аналитическая платформа для распределенной обработки и анализа данных.
    * **Spark SQL:** Используется для выполнения структурированных аналитических запросов с использованием стандартного SQL-синтаксиса.
    * **PySpark:** Python API для Spark, применяемый для программной ETL-обработки данных и взаимодействия с DataFrame API.
    * **Spark MLlib:** Библиотека машинного обучения для Spark, использованная для построения и оценки модели классификации.

* **Python:** Основной язык программирования для разработки всех скриптов и Jupyter Notebook.

* **Jupyter Lab:** Интерактивная среда разработки, обеспечивающая удобство выполнения кода, отладки и визуализации результатов.

* **Matplotlib & Seaborn:** Библиотеки Python для создания статических и информативных графиков, используемых для визуализации ключевых показателей.

## Датасет

В проекте используется публичный датасет **COVID-19 Chest X-Ray Dataset**, доступный на GitHub:
<https://github.com/ieee8023/covid-chestxray-dataset.git>

Датасет содержит:

* **Изображения:** Рентгеновские снимки (PNG/JPEG) пациентов с различными диагнозами, включая COVID-19, пневмонию и другие патологии.

* **Метаданные:** Файл `metadata.csv`, содержащий подробную информацию о каждом снимке и пациенте, включая:
    * `patientid`: Уникальный идентификатор пациента.
    * `age`: Возраст пациента.
    * `sex`: Пол пациента.
    * `finding`: Диагноз, связанный со снимком.
    * `view`: Проекция рентгеновского снимка (например, PA, AP).
    * `date`: Дата проведения исследования.

**Важное примечание:** Исходные файлы датасета (изображения и `metadata.csv`) **НЕ ВКЛЮЧЕНЫ** в данный репозиторий из-за их большого размера и условий лицензирования. Также, в связи с тем, что проект разворачивался в Hadoop для получения навыков, данные хранятся в HDFS.

## Структура проекта
```
├── Covid_analysis.ipynb          # Основной Jupyter Notebook с полным циклом анализа данных 
├── LogisticRegression.ipynb      # Jupyter Notebook с реализацией модели логистической регрессии
├── RandomForestClassifier.ipynb  # Jupyter Notebook с реализацией модели случайного леса
├── SparkSQL.ipynb                # Jupyter Notebook с примерами SQL-запросов на Spark SQL
├── Сharts_covid.ipynb            # Jupyter Notebook с кодом для генерации всех визуализаций
├── presentation_images/          # Папка с изображениями слайдов презентации
├── README.md                     # Этот файл с описанием проекта
└── .gitignore                    # Файл для исключения временных файлов и больших данных из Git
```
## Развертывание инфраструктуры

Для запуска проекта требуется кластер Hadoop и Spark. **Я осуществила самостоятельное развертывание и настройку всех необходимых компонентов на базе WSL (Ubuntu)**. Рекомендуется использовать Docker-контейнеры для локального тестирования и более простого воспроизведения среды.

1.  **Установка компонентов:**
    Установка Apache Hadoop, Apache Spark и всех необходимых Python-библиотек производилась вручную в среде WSL (Ubuntu), следуя официальной документации.
    * **Hadoop Version:** `3.3.6`
    * **Spark Version:** `3.5.1`
    * **Python Version:** `3.10.12`
    * **Java Version:** `11.0.27`
    * **Ключевые Python библиотеки:**
        * `pyspark==3.5.1`
        * `pandas==2.3.0`
        * `matplotlib==3.10.3`
        * `seaborn==0.13.2`

2.  **Настройка доступа к Web UI:**
    Доступ к веб-интерфейсам (Hadoop NameNode, Spark History Server, Jupyter Lab) был настроен согласно стандартным рекомендациям по конфигурированию, используя следующие адреса:
    * Hadoop NameNode UI: `http://localhost:9870`
    * Spark History Server UI: `http://localhost:18080`
    * Jupyter Lab: `http://localhost:8888`

3.  **Проверка работы HDFS CLI:**
    Работа с HDFS CLI была проверена путем загрузки и чтения тестовых файлов, что подтвердило корректность развертывания распределенной файловой системы.


   ###  1. Запуск проекта и анализ

Все этапы проекта реализованы в Jupyter Notebook `covid_analysis.ipynb`.

1.  **Откройте Jupyter Lab:** Перейдите по адресу `http://localhost:8888` в вашем браузере (или по другому порту, если он настроен).

2.  **Откройте `covid_analysis.ipynb`:** Найдите и откройте этот файл в интерфейсе Jupyter Lab.

3.  **Последовательно запускайте ячейки:**

    ### 2. Предобработка данных (ETL)

    * **Цель:** Очистка, стандартизация и обогащение исходных метаданных.

    * **Достижения:**

        * **Заполнение пропусков:** Реализованы индивидуальные стратегии для числовых (`age_numeric`, `temperature`, `pO2_saturation`, `leukocyte_count`, `neutrophil_count`, `lymphocyte_count` — заполнение медианой/средним) и категориальных полей (`sex`, `RT_PCR_positive`, `survival` — заполнение модой или "UNKNOWN").

        * **Удаление дубликатов:** Все повторяющиеся записи были удалены.

        * **Унификация диагнозов:** Создан новый признак `finding_unified` (например, "covid-19", "other pneumonia", "tuberculosis", "no finding", "other finding").

        * **Создание новых аналитических признаков:** Введены `age_group` (child, adult, senior), `is_covid` (бинарный флаг для COVID-19) и извлечены `year`, `month`, `day` из поля `date` с обработкой множественных форматов.

        * **Комплексный анализ качества данных:** Проведен анализ распределения пропущенных значений, выявлены и обработаны аномалии, что задокументировано в выводе Jupyter Notebook.

        * **Сохранение оптимизированной структуры:** Очищенные данные сохранены в HDFS по пути `/covid_dataset/metadata_optimized/` в формате **Parquet**. При этом реализовано **партиционирование по `year` и `month`** и **бакетирование по `finding_unified` и `sex`**, что значительно ускоряет аналитические запросы.

    ### 3. SQL-аналитика

    * **Цель:** Проведение глубокого анализа данных с использованием Spark SQL.

    * **Достижения:** Разработано **8 аналитических SQL-запросов**, демонстрирующих широкий спектр возможностей Spark SQL:

        * **Запросы с агрегацией и фильтрацией:** Распределение диагнозов по полу, топ-локации по случаям COVID-19, процент COVID-случаев по месяцам.

        * **Запросы с оконными функциями:** Динамика накопительных случаев COVID-19 (`SUM() OVER(...)`), скользящее среднее возраста пациентов (`AVG() OVER(...)`).

        * **Сложные соединения таблиц:** Продемонстрировано через **самосоединение (`Self-Join`)** для поиска пар пациентов с общими характеристиками, но значительной разницей в возрасте.

        * **Аналитические подзапросы:** Использованы для более сложной фильтрации и ранжирования данных (например, поиск локации с самой высокой средней температурой среди активных).

    ### 4. Обработка в PySpark и Машинное обучение

    * **Цель:** Применение методов машинного обучения для выявления закономерностей и построения предсказательной модели.

    * **Достижения:**

        * **Подготовка данных для ML:** Категориальные признаки были преобразованы с помощью `StringIndexer` и `OneHotEncoder`, а все признаки собраны в единый вектор с помощью `VectorAssembler` в рамках Spark ML Pipeline.

        * **Построение модели классификации:** Обучена модель **Random Forest Classifier** для предсказания наличия COVID-19 (`is_covid`) на основе метаданных.

        * **Оценка производительности:** Модель достигла **высокого показателя Area Under ROC (AUC) = 0.9054** на тестовой выборке, что свидетельствует о её отличной предсказательной способности.

        * **Анализ важности признаков:** Выявлены наиболее важные признаки для предсказания: **температура, количество лимфоцитов и сатурация кислорода**, что согласуется с клиническими данными.

    ### 5. Визуализация

    * **Цель:** Наглядное представление ключевых эпидемиологических показателей и характеристик пациентов.

    * **Достижения:** Созданы **4 визуализации** с использованием библиотек **Matplotlib и Seaborn**, которые включают:

        * Круговую диаграмму распределения диагнозов.

        * Столбчатую диаграмму распределения случаев COVID-19 по полу.

        * Линейный график динамики случаев COVID-19 по годам и месяцам.

        * Столбчатую диаграмму топ-5 локаций по количеству случаев COVID-19.

        * Эти графики эффективно интерпретируют полученные аналитические выводы.

## Рекомендации по улучшению системы

Для дальнейшего развития и повышения эффективности аналитической платформы можно рассмотреть следующие направления:

* **Расширение и обогащение данных:** Интеграция дополнительных клинических данных (например, история болезни, сопутствующие заболевания) для повышения точности анализов и моделей.

* **Дальнейшая оптимизация Hive/Spark:** Создание внешних таблиц Hive, использование агрегированных представлений (Materialized Views) для ускорения часто используемых отчетов.

* **Интеграция компьютерного зрения:** Разработка и внедрение моделей **компьютерного зрения** для автоматической классификации самих медицинских изображений (рентгеновских снимков) на предмет патологий, что позволило бы создать более мощную и автоматизированную диагностическую систему.

## Презентация
![Слайд 1](presentation_images/1.png)
![Слайд 2](presentation_images/2.png)
![Слайд 3](presentation_images/3.png)
![Слайд 4](presentation_images/4.png)
![Слайд 5](presentation_images/5.png)
![Слайд 6](presentation_images/6.png)
