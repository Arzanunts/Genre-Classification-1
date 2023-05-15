# Genre-Classification
Использование методов МО для классификации жанров
[https://disk.yandex.ru/d/z_QRcU0mWkp87Q](Spotify+Y.Music songs)
Задача:
Классифицировать жанры, используя классические методы машинного обучения. Будем использовать библиотеку `librosa` 
Содержание проекта:
*[librosa_preview.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/librosa_preview.ipynb) - тетрадь про библиотеку librosa и различные методы librosa.feature. Анализ спектрограмм и их визуализация
*[models.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/models.ipynb) - модели на основе датасета spotify.csv. XGB, LGBM, Catboost, SVM, RandomForest etc без fine tuning. 
*[parsing.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/parsing.ipynb) - тетрадь, содержащая парсинг Yandex.Music и Spotify(API).
*[Dataset.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/Dataset.ipynb) - сборка датасета с данных парсинга.(Обработка музыки через librosa, создание датафрейма) 

