---
title: Мелкие радости - удаление двойного заголовка таблицы
date: 2021-07-11
image: images/blog/blog_014_foto.jpg
author: Smile
---

> *Рвав-рвав, сегодня я -- собака-разузнака!*
>
> *Перед вами -- 9-я заметка из нашего цикла "Мелкие радости", ниже мы рассмотрим такую проблему, как обработка двойной шапки в исходных данных.*
>
> *Обычно подобна штукенция присутствует в данных при использовании файловой выгрузки (если она не самописная, конечно) из "материнской" системы, например, 1С и пр.*
>
> *В общем, сегодня мы будем совместно познавать Power Query, используя, так сказать, классику жанра, поскольку подобная задача далеко не нова…*


**Пример:**

В качестве исходных данных файл MS Excel, с таблицей, содержащий двойной заголовок следующего вида:

![blog_014_screen_01](https://kkadikin.ru/images/blog/blog_014_screen_01.jpg)


**Задача:**

Трансформировать исходную таблицу таким образом, чтобы устранить двойной заголовок, то есть, в итоге, таблица должна стать плоской.


**Процесс разработки:**

**<li>** Для начала необходимо импортировать данные в Power BI:

![blog_014_screen_02](https://kkadikin.ru/images/blog/blog_014_screen_02.jpg)

**<li>** Удалить все шаги до шага "Навигация", поскольку в настройке "по умолчанию" при загрузке происходит автоматическое повышение заголовков и автоматическое присвоение типов данных:

![blog_014_screen_03](https://kkadikin.ru/images/blog/blog_014_screen_03.jpg)

**<li>** Транспонировать таблицу, использовав на вкладке "Преобразование" кнопку "Транспонировать":

![blog_014_screen_04](https://kkadikin.ru/images/blog/blog_014_screen_04.jpg)

**<li>** Объединить первые 2 столбца, поскольку шапка таблицы содержит 2 уровня, использовав на вкладке "Преобразование" кнопку "Объединить столбцы":

![blog_014_screen_05](https://kkadikin.ru/images/blog/blog_014_screen_05.jpg)

> *Рвав-рвав, при объединении столбцов необходимо указать какой-нибудь разделитель, в нашем случае это знак равенства ( «=» ).*

**<li>** Транспонировать получившуюся таблицу обратно:

![blog_014_screen_06](https://kkadikin.ru/images/blog/blog_014_screen_06.jpg)

**<li>** Поставить заголовки столбцов, например, воспользовавшись функционалом повышения заголовков:

![blog_014_screen_07](https://kkadikin.ru/images/blog/blog_014_screen_07.jpg)

**<li>** Повышение заголовков потянет за собой шаг изменения типа данных, который можно оставить.

**<li>** Следующим шагом необходимо отменить свертывание «дополнительных» столбцов, для этого на   вкладке "Преобразование" следует воспользоваться кнопкой "Отменить свертывание столбцов", использовав при этом функцию "Отменить свертывание других столбцов":

![blog_014_screen_08](https://kkadikin.ru/images/blog/blog_014_screen_08.jpg)

**<li>** Разделить столбец "Атрибут" по имеющемуся разделителю, то есть знаку равенства ( «=») , который использовался ранее в качестве разделителя, воспользовавшись кнопкой "Разделить столбец" на вкладке "Главная":

![blog_014_screen_09](https://kkadikin.ru/images/blog/blog_014_screen_09.jpg)

**<li>** Присвоить окончательные название получившимся столбцам:

![blog_014_screen_10](https://kkadikin.ru/images/blog/blog_014_screen_10.jpg)

**<li>** Далее следует заменить значение "Пусто" на значение "null" в столбце "Город", воспользовавшись кнопкой "Замена значений" на вкладке "Преобразование":

![blog_014_screen_11](https://kkadikin.ru/images/blog/blog_014_screen_11.jpg)

**<li>** Последним шагом является корректное заполнение ячеек, содержащих значение "null", по столбцу "Город". Данное действие можно выполнить автоматически, выбрав опцию "Заполнить вниз", имеющуюся у кнопки "Заполнить" на вкладке "Преобразование":

![blog_014_screen_12](https://kkadikin.ru/images/blog/blog_014_screen_12.jpg)

**<li>** После последовательного выполнения перечисленных шагов для сохранения внесенных изменений необходимо нажать кнопку "Закрыть и применить", расположенную на закладке "Главная".

> *Рвав-рвав, извините, но я уже все, лапы ломит, и хвост отваливается…*
>
> *Ваш Смайл*

> *P.S. Рвав-рвав, после публикации ссылки на Facebook, и, сообетственно, просмотра материала, поступило предложение заполнить значения "null" сразу после 1-го транспонирования. Я с этим согласен, так, действительно, у нас будет потом чуть меньше шагов, но текст оставляю в оригинальном виде.*
>
> *P.P.S. Рва-ва-вав, собака Смайл прислушивается к аудитории (по крайней мере, иногда, и к некоторым товарищам :-Р)*