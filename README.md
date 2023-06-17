# Genre-Classification

### ROC-AUC - целевая метрика. ROC-AUC для валидационной - 0.8339

Использование методов МО для классификации жанров
[validation+Spotify+Y.Music songs](https://disk.yandex.ru/d/z_QRcU0mWkp87Q)

### Задача:  
Классифицировать жанры музыки, используя классические методы машинного обучения. Наш подход к её решению заключается в предварительном извлечении признаков из звуковой дорожки посредством библиотеки `librosa`, затем разбиении каждой песни на трёхсекундные непересекающиеся отрезки и построении модели, что умеет классифицировать трёхсекундные кусочки. Итоговое предсказание для песни это жанр, который чаще всего встречается в 'predict_list', где 'predict_list' - прогнозы к каждому трёхсекндному отрезку, из кототорых состоит трэк.

### Содержание проекта:
* [librosa_preview.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/librosa_preview.ipynb) - тетрадь про библиотеку librosa и различные методы librosa.feature. Анализ спектрограмм и их визуализация

Пример визуализации:

<image src="pics/chroma.png" alt="chroma">

* [parsing.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/parsing.ipynb) - тетрадь, содержащая парсинг Yandex.Music и Spotify(API).
* [Dataset.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/Dataset.ipynb) - сборка датасета с данных парсинга.(Обработка музыки через librosa, создание датафрейма)
* [spotify.csv](https://github.com/TimRicMus/Genre-Classification/blob/main/spotify.csv) - датасет из песен со Spotify. 
* yandex.csv - датасет из песен с Yandex Music
* final.csv - объединенный датасет(Spotify+Y.Music)
* valid.csv - датасет для теста
* [Yandex_dataset.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/Yandex_dataset.ipynb) - тетрадь, содержащая сборку датасета yandex.csv
* [Dataset_valid.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/Dataset_valid.ipynb) - тетрадь со сборкой валидационной выборки  
* [Project_models.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/Project_models.ipynb) - тетрадь Feature Engineering + EDA
* [hyperparameters.ipynb](https://github.com/TimRicMus/Genre-Classification/blob/main/hyperparameters.ipynb) - подбор гиперпараметров + квантизация  
  
Рекомендуем просматривать работу в таком порядке:
  1) parsing.ipynb
  2) librosa_preview.ipynb
  3) Dataset.ipynb
  4) Yandex_dataset.ipynb
  5) Dataset_valid.ipynb
  6) Project_models.ipynb
  7) hyperparameters.ipynb

### Exploratory data analysis and feature engineering 
* EDA
  
В качестве инструмента предварительного отбора признаков, извлеченных из звукововой дорожки с помощью 'librosa', мы решили использовать дисперсионный анализ. Идея заключается в том, что если призанак дейтвительно влияет на целевую переменную, то его распределение (а конкретнее мат. ожидание) будет разным для разных жанров. Однако, попытавшись использовать ANOVA, мы столкнулись с большим количеством трудностей. Одна из них снизу :)

<image src="pics/qqplot.png" alt="qqplot">  

По мере решения проблем, связанных с предпосылками для ANOVA, мы проанилизировали распределения наших признаков и пришли к выводу, что лучший выход из положения - тест Краскела-Уоллиса, и он отработал на ура. Так, например, выглядят доверительные интервалы для средних по жанрам для признака, для которого согласно тесту средние между группами должны различаться.  

<image src="pics/means.png" alt="means">

* Генерация признаков
  
Один из лучших способов улучшить качество модели в ситуации, в которой нам не очень важна интерпретуемость признаков, это генерация новых на основе существующих.  
Так, мы попробовали нагенереировать полиномиальные комбинации имеющихся признаков вплоть до 3 степени, налепив на них экспоненты и синусы. Для отбора лучших из них, мы решили использовать величину уверенности теста Краскелла-Уоллиса в присутствии влияния признака на целевую переменную. 
На основе этого подхода мы проверили различные способы генерации и отбора признаков и по итогу даже немного улучшили качество модели.

* Квантизация признаков

Мы попробовали использовать ещё один подход - мы кластеризовали объекты с помощью метода K-means и создали новый категориальный признак, отвечающий за принадлежность к кластеру. При этом мы попробовали это сделать с использованием SMOTE, нормировки и без них. Для визуализации кластерного анализа мы использовали `UMAP` - иснтрумент, отвечающий за снижение размерности нашей матрицы до двумерной плоскости. 

  <image src="pics/umap.png" alt="umap">






