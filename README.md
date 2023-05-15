# Genre-Classification
Использование методов МО для классификации жанров
[Spotify+Y.Music songs](https://disk.yandex.ru/d/z_QRcU0mWkp87Q)
Задача:
Классифицировать жанры, используя классические методы машинного обучения. Будем использовать библиотеку `librosa` для Feature Engineering.
Содержание проекта:
* [librosa_preview.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/librosa_preview.ipynb) - тетрадь про библиотеку librosa и различные методы librosa.feature. Анализ спектрограмм и их визуализация
* [models.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/models.ipynb) - модели на основе датасета spotify.csv. XGB, LGBM, Catboost, SVM, RandomForest etc без fine tuning. 
* [parsing.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/parsing.ipynb) - тетрадь, содержащая парсинг Yandex.Music и Spotify(API).
* [Dataset.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/Dataset.ipynb) - сборка датасета с данных парсинга.(Обработка музыки через librosa, создание датафрейма) 
* [spotify.csv](https://github.com/TimRicMus/Genre-Classification/blob/main/spotify.csv) - готовый датасет для обучения. 
Для тестирования гипотез будет использоваться датасет из песен Y.Music
Гипотезы:
* ANOVA - статистический метод, используемый для анализа различий между средними значениями двух или более групп данных.
* Кластерный анализ - метод, позволяющий группировать объекты на основе их сходства в пределах одной группы и различия между группами.
* Анализ главных компонент (PCA) - метод, используемый для снижения размерности данных путем проекции их на новые некоррелированные переменные, называемые главными компонентами.
* Влияет ли язык в музыке на классификацию жанра.



