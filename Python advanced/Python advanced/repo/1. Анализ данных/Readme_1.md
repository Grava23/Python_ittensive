Часть 1: анализ данных

#numpy и pandas
Задание

возьмите данные по вызовам пожарных служб в Москве за 2015-2019 годы:
https://video.ittensive.com/python-advanced/data-5283-2019-10-04.utf.csv
Получите из них фрейм данных (таблицу значений). По этому фрейму вычислите среднее значение вызовов пожарных машин в месяц в одном округе Москвы, округлив до целых
Примечание: найдите среднее значение вызовов, без учета года

Решение:
1)	подключаем библиотеку pandas
2)	получаем данные, в качестве разделителя указываем точку с запятой
3)	в серии данных, в которой указано количество звонков в месяц, в одном административном округе, мы получаем среднее значение с помощью метода mean()
4)	затем выводим его, как целое число

#Индексы и объединение фреймов
Задание

Получите данные по безработице в Москве:
https://video.ittensive.com/python-advanced/data-9753-2019-07-25.utf.csv
Объедините эти данные индексами (Месяц/Год) с данными из предыдущего задания (вызовы пожарных) для Центральный административный округ:
https://video.ittensive.com/python-advanced/data-5283-2019-10-04.utf.csv
Найдите значение поля UnemployedMen в том месяце, когда было меньше всего вызовов в Центральном административном округе.


Решение:
1)	получаем необходимые для нас данные о вызовах
2)	в данных вызовов пожарных по округам, в качестве индексов используем округа, год и месяц
3)	в данных о работоспособности населения, качестве индексов используем год и период
4)	переименовываем индексы, на идентичные как в данных о вызовах
5)	выбираем все значения, где в названии присутствует "Центральный административный округу"
6)	объединяем два набора данных по левым и правым индексам
7)	отбрасываем текущий индекс
8)	назначаем новый индекс по числу вызовов
9)	сортируем данные по этому индексу
10)	выведем одно значение из серии "UnemployedMen", начиная с нулевого индекса

#Фильтрация и изменение данных

Задание
Получите данные по безработице в Москве:
https://video.ittensive.com/python-advanced/data-9753-2019-07-25.utf.csv
Найдите, с какого года процент людей с ограниченными возможностями (UnemployedDisabled) среди всех безработных (UnemployedTotal) стал меньше 2%.
Решение:
1)	подключаем библиотеку pandas
2)	Узнаём, чему равно 2 процента, и выбираем те значения которые больше двух с помощью lambda функции, 100 умножаем на произведение между UnemployedDisabled и UnemployedTotal
3)	в качестве индекса используем серию данных "Year"
4)	сортируем данные по индексу
5)	выбираем все значения до первого, начиная с нулевого
6)	выводим ответ

#Линейная регрессия

Задание
Возьмите данные по безработице в городе Москва:
video.ittensive.com/python-advanced/data-9753-2019-07-25.utf.csv
Сгруппируйте данные по годам, и, если в году меньше 6 значений, отбросьте эти годы.
Постройте модель линейной регрессии по годам среднего значения отношения UnemployedDisabled к UnemployedTotal (процента людей с ограниченными возможностями) за месяц и ответьте, какое ожидается значение процента безработных инвалидов в 2020 году при сохранении текущей политики города Москвы?
Ответ округлите до сотых. Например, 2,32
Решение:
1)	подключаем необходимые фреймворки
2)	рассчитываем отношение в процентах
3)	для фильтрации, выполняем группировку по году, используем метод фильтрации с лямбда функцией которая принимает на вход группу данных
4)	считаем число строк, которое вошло в группу данных x, и это число строк должно быть больше 5, так как фильтр возвращает не группу, а сами данные, ещё раз группируем и находим среднее значение согласно условию
5)	изменяем форму, и преобразуем данные в двумерный массив
6)	загружаем модель линейной регрессии
7)	добавляем в неё наши значения
8)	добавляем график модели
9)	вычисляем значение для 2020г, делаем из него двумерный массив
10)	выводим ответ