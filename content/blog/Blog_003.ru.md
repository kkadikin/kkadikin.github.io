---
title: Мелкие радости - нюансы выбора значения в срезе
date: 2020-07-04
image: images/blog/blog_003_foto.jpg
author: Smile
---

> *Рвав-рвав, сегодня я -- собака-мечтатель!*
>
> *А поскольку я мелкий эгоист (мелкий в плане размера, а не эгоизма!), то в связи с существующим настроением начинаю реализовывать свою мечту:*
>
> *уря-уря, мы начинаем публиковать контент под названием "Мелкие радости",  который был неосторожно обещан в статье [Использование мер в качестве переключателя](https://kkadikin.ru/ru/blog/article_003/).*
>
> *Спешу напомнить, что здесь планируется размещать материал о неких хитростях по принципу "Мелочь, а приятно".*
>
> *Итак, поехали, 1-я заметка представлена ниже.*

**Пример:** 

Есть таблица, содержащая некий список проектов и ответственного менеджера.

![blog_003_screen_1](https://kkadikin.ru/images/blog/blog_003_screen_1.jpg)

**Задача:**

Вывести количество проектов по каждому менеджеру при помощи элемента "Card" ("Карточка") .

> *Вроде бы, все просто :-)*

**Решение:**

**<li>** Создаем фильтр по менеджеру;

**<li>** Создаем карточку для менеджера;

**<li>** Создаем карточку для количества проектов, значение которой можно посчитать различными способами, например, мерой (Количество проектов = COUNTROWS('Datset'), или при помощи свойства "Count" на значении элемента.

При фильтрации данных кажется, что все отлично, начинаем радоваться, поскольку у 1-го менеджера 3 проекта, а у 2-го -- 2.

![blog_003_screen_2](https://kkadikin.ru/images/blog/blog_003_screen_2.jpg)

![blog_003_screen_3](https://kkadikin.ru/images/blog/blog_003_screen_3.jpg)

Но как только пользователь не выберет ничего, то выяснится, что радость была преждевременной, поскольку, несмотря на правильное общее количество проектов -- 5, в карточке менеджера будет отображено значение, равное:

**<li>** "Менеджер 1", если в свойствах значения элемента стоит дефолтный вариант "First" ("Первый");

**<li>** "Менеджер 2", если в свойствах значения элемента стоит ариант "Last" ("Последний").

![blog_003_screen_4](https://kkadikin.ru/images/blog/blog_003_screen_4.jpg)

Возможным выходом из этой ситуации является дополнительная настройка фильтра, а именно включение настройки "Single select" ("Единичное выделение"), но тогда значения в карточках будут всегда отфильтрованы по умолчанию в разрезе менеджеров, что "не есть хорошо".

> *Р-р-р-р-р-р, собаке Смайлу подобная ситуация активно не нравится, и поэтому он подготовил собственное решение, а именно, решил вывести текст-предупреждение для пользователя о том, что ему необходимо выбрать конкретное значение.*

**Лайфхак от хитрой собаки:** 

```dax
Менеджер =
VAR _Manager =
    VALUES ( Datset[Менеджер проекта] )
VAR _QuantityRows =
    COUNTROWS ( _Manager )
VAR _Result =
    IF ( _QuantityRows > 1, "Выберите менеджера", _Manager )
RETURN
    _Result
```

Как вы можете убедиться, подобная штука поможет вам избежать несогласованности при визуализации данных, в случае, когда в фильтре ничего не выбрано.

![blog_003_screen_5](https://kkadikin.ru/images/blog/blog_003_screen_5.jpg)

> *Рвав-рвав, на этом все, пойду на праздник, авось, чего перепадет...*
>
> *Ваш Смайл*
>
> *P.S. Любителям понажимать на кнопочки -- увы, в рубрике "Мелкие радости" вам облом :-Р*
>
> *P.P.S. Безмерно уважаемые двуногие предложили еще более изящный вариант:*

```dax
Менеджер =
SELECTEDVALUE ( Dataset[Менеджер проекта], "Несколько менеджеров" )
```