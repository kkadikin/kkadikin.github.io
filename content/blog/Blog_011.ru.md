---
title: Мелкие радости - выгрузка большого объема данных
date: 2020-11-22
image: images/blog/blog_011_foto.jpg
author: Smile
---

> *Рвав-рвав, сегодня я -- собака-курочка!*
>
> *Перед вами -- 7-я заметка из нашего цикла "Мелкие радости", и сегодня мы рассмотрим такой наболевший вопрос, как выгрузка большого объема данных из MS Power BI.*
>*В последнее время часто попадаются ситуации, когда нашу любимую систему используют как некое промежуточное средство, для выгрузки данных в MS Excel в целях дальнейшего анализа (с построением, опять-таки, сводных таблиц и прочими делами).*
>
> *Свое особое мнение на этот счет могу высказать отдельно, и не здесь, а пока, как говорится: "...Ну надо так надо!"*

**Пример:**

В качестве исходных данных имеется набор, содержащий всего один столбец -- "Номер", в котором, однако, содержится больше 150 тысяч значений:

![blog_011_screen_1](https://kkadikin.ru/images/blog/blog_011_screen_1.jpg)


**Задача:**

Получить указанный набор значений в MS Excel.


>*Рвав-рвав, в выполнении данной задачи нам поможет такой инструмент, как DAX Studio.* 
>
>*Количество записей в объеме "150 010" взято не "с потолка", а в связи с тем, что, например, с облаке (служба Power BI Service), существует ограничение на выгрузку в объеме "150 000" для файла Excel, и "30 000" для файла CSV.*


**Реализация требований:**

**<li>** Открываем файл Power BI, содержащий модель данных.

**<li>** Запускаем DAX Studio:

![blog_011_screen_2](https://kkadikin.ru/images/blog/blog_011_screen_2.jpg)

**<li>** Устанавливаем переключатель в пункт "PBI / SSDT Model":

![blog_011_screen_3](https://kkadikin.ru/images/blog/blog_011_screen_3.jpg)

**<li>** Устанавливаем переключатель в пункт "Connect".

**<li>** В открывшемся окне запроса пишем нужную команду "EVALUATE" с имененем нужной таблицы, в нашем случае -- 'Dataset':

![blog_011_screen_4](https://kkadikin.ru/images/blog/blog_011_screen_4.jpg)

**<li>** Запускаем запрос на выполнение при помощи кнопки "Run" (Путь: Закладка Home -> Кнопка "Run"), ну или на клавиатуре -- "F5", в результате выполнения запроса в нижней части экрана в разделе "Results") появятся данные:

![blog_011_screen_5](https://kkadikin.ru/images/blog/blog_011_screen_5.jpg)

**<li>** Указываем способ сохранения данных при помощи кнопки "Output" (Путь: Закладка Home -> Кнопка "Output" -> Кнопка "File").

**<li>** В результате описанных действий в нижней части экрана в разделе "Results" появится сообщение следующего вида:

![blog_011_screen_6](https://kkadikin.ru/images/blog/blog_011_screen_6.jpg)

**<li>** Повторно запускаем запрос на выполнение.

**<li>** В открывшемся окне указываем желаемое има файла, и его тип:

![blog_011_screen_7](https://kkadikin.ru/images/blog/blog_011_screen_7.jpg)

> *Рвав-рвав, окно сохранения у вас может отличаться от рисунка, поскольку здесь папки скрыты -- у собак свои секреты!"*
>
> *Также, в качестве рекомендации для сохранения лучше выбирать кодировку UTF-8.*

**<li>** Нажать кнопку "Сохранить".

**<li>** Открыть получившийся файл при помощи MS Excel и проверить результат.


> *Рвав-рвав, DAX Studio всем в лапы!*
>
> *Ваш Смайл*