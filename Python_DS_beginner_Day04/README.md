# DAY 04 – Школа 21
## Кластеризация и методы снижения размерности
В рамках этого дня вы узнаете, что такое обучение без учителя, и научитесь использовать различные методы кластеризации.

## Оглавление

1. [Глава I](#глава-i) \
    1.1. [Преамбула](#преамбула)
2. [Глава II](#глава-ii) \
    2.1. [Общая инструкция](#общая-инструкция)
3. [Глава III](#глава-iii) \
    3.1. [Цели](#цели)
4. [Глава IV](#глава-iv) \
    4.1. [Задание](#задание)
5. [Глава V](#глава-v) \
    5.1. [Сдача работы и проверка](#сдача-работы-и-проверка)

## Глава I
### Преамбула

В машинном обучении есть методы, которые позволяют решать задачи обучения "без учителя". Это такой класс задач, когда у нас нет четких ответов для объектов и, больше того, у нас даже нет обучающей выборки. Самая часто встречаемая задача этого класса - кластеризация. Здесь мы имеем набор объектов с их характеристиками (признаками), но у нас нет информации, каким классам они принадлежат или в какое числовое значение они должны отображаться. Нам просто нужно разделить их на группы так, чтобы похожие объекты оказались в одном кластере, а различные объекты - в разных кластерах. А вот принцип, по которому мы будем считать объекты похожими, нам нужно определить самостоятельно.

Сегодня вы изучите некоторые методы кластеризации выборок объектов, а также познакомитесь с методами снижения размерности признакового пространства. Последняя группа методов может быть нам полезна, когда объекты описываются очень большим количеством признаков, и нам тяжело обрабатывать их все. Здесь наша задача - описать объекты меньшим количеством признаков, но так, чтобы относительные расстояния между объектами в старом признаковом пространстве как можно точнее сохранились и в новом.


## Глава II
### Общая инструкция

Методология Школы 21 может быть не похожа на тот образовательный опыт, который с вами случался ранее. Ее отличает высокий уровень автономии: у вас есть задача, вы должны ее выполнить. По большей части вам нужно будет самим добывать знания для ее решения. Второй важный момент – это peer-to-peer обучение. В образовательном процессе нет преподавателей и экспертов, перед которыми вы защищаете свой результат. Вы это делаете перед таким же учащимися, как и вы сами. У них есть чек-лист, который поможет им выполнить приемку вашей работы качественно.

Роль Школы 21 заключается в том, чтобы обеспечить через последовательность заданий и оптимальный уровень поддержки такую траекторию обучения, при которой вы освоите не только hard skills, но и научитесь самообучаться.

* Не доверяйте слухам и предположениям о том, как должно быть оформлено ваше решение. Этот документ является единственным источником, к которому стоит обращаться по большинству вопросов.
* Ваше решение будет оцениваться другими учащимися бассейна.
* Подлежат оцениванию только те файлы, которые вы выложили в GIT.
* В вашей папке не должно быть лишних файлов – только те, что были указаны в задании.
* Есть вопрос? Спросите коллегу справа. Не помогло? Спросите коллегу слева.
* Не забывайте, что у вас есть доступ к интернету и поисковым системам.
* Обсуждение заданий можно вести и в Slack бассейна.
* Будьте внимательные к примерам, указанным в этом документе – они могут иметь важные детали, которые не были оговорены другим способом.
* И да пребудет с вами Сила!



## Глава III
### Цели

Наша цель - научиться кластеризовать выборку с использованием библиотеки sklearn, а также научиться применять методы понижения размерности признакового пространства для упрощения решения задач машинного обучения.


## Глава IV
### Задание

Сегодня вы будете работать с неразмеченными данными. Вся работа у нас идет в Jupyter Notebooks / Google Colab. Ноутбук этого дня вы сможете найти здесь: `src/d04_task.ipynb`.


Что нужно сделать:
1. Провести кластеризацию данных из прилагаемого файла. Выбрать количество кластеров для выборки по методам локтя, silhouette_score, calinski_harabasz_score и davies_bouldin_score. Обучить KMeans с разбиением на два кластера, провести оценку результата с помощью classification_report. Оценить результат кластеризации с помощью функции metrics4() и заполните соответствующий столбец таблицы итогов кластеризации m4.
2. Обучить общую модель агломеративной кластеризации. Выбрать количество кластеров по дендрограмме. Обучить модель агломеративной кластеризации для двух кластеров. Оценить качество кластеризации и записать результат в таблицу итогов.
3. Обучить модель PCA для 6 главных компонент. Визуализировать сохраненную дисперсию. Определить количество главных компонент, сохраняющих не менее 90% дисперсии. Обучить модель для двух главных компонент и визуализировать данные.
4. Визуализировать данные с помощью метода t-SNE при различных значениях perplexity.
5. Написать функцию add_a_ov, которая исправляет ошибку 19-го кластера. Внедрить эту функцию в функцию viz_dbscan. Обучить модель DBSCAN с параметрами по умолчанию и визуализировать результат. Подберите гиперпараметр eps. Провести визуализацию зависимости количества кластеров от параметра eps. Обучить модель DBSCAN с таким параметром eps, чтобы получить разбиение на два кластера. Визуализировать результат. Проанализировать соответствие полученных кластеров классам. Оценить качество кластеризации и записать результат в таблицу. Сделать выводы по всем методам кластеризации.



## Глава V
### Сдача работы и проверка

1. Вам нужно загрузить в GIT в папку `src` свой Jupyter Notebook.
    1. Он должен содержать в себе весь требуемый код.
    2. Он должен называться `d04_desc.ipynb`.

