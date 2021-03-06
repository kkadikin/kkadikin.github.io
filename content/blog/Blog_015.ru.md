---
title: Мелкие радости - управление раcчетом подитогов
date: 2021-07-17
image: images/blog/blog_015_foto.jpg
author: Smile
---

> *Рвав-рвав, сегодня я -- собака-управляка!*
>
> *Перед вами -- 10-я заметка из нашего цикла "Мелкие радости", ниже мы рассмотрим такую задачу, как вывод разных составляющих при расчете подитогов в матрице, в зависимости от уровня.*


**Пример:**

В качестве исходных данных имеется набор, содержащий товарные позиции, а именно группу товаров, бренд и цену:

![blog_015_screen_1](https://kkadikin.ru/images/blog/blog_015_screen_1.jpg)


**Задача:**

Построить матрицу таким образом, чтобы в зависимости от уровня подитога выводился определенный расчет, например, обычная сумма или средняя.


**Процесс разработки:**

**<li>** Для начала необходимо построить обычную матрицу с построчной группировкой по группе товара и бренду:

![blog_015_screen_2](https://kkadikin.ru/images/blog/blog_015_screen_2.jpg)

**<li>** После этого необходимо написать меру, которая бы имела в себе проверку на уровень данных, а также указание на применение необходимых расчетов:

```dax
Расчет по уровням =
VAR _Average =
    AVERAGE ( 'Таблица'[Цена] )
VAR _Amount =
    SUM ( 'Таблица'[Цена] )
RETURN
    SWITCH (
        TRUE (),
        ISINSCOPE ( 'Таблица'[Бренд] ), _Amount,
        ISINSCOPE ( 'Таблица'[Группа] ), _Average,
        FORMAT ( _Amount, "## ### ₽" )
    )
```

> *Рвав-рвав, в данной формуле идет раздельный расчет с проверкой уровня при помощи функции ISINSCOPE, а также добавлено форматирование общего итога (для демонстрации возможности отдельного управления).*
>
> *Формула, надо сказать, простая, главное начать думать "в правильную сторону", с чем могут быть определенные проблемы, поскольку сначала собака Смайл раздумывал о том, как отделить общий итог от промежуточного.*

**<li>** Проверить получившийся результат:

![blog_015_screen_3](https://kkadikin.ru/images/blog/blog_015_screen_3.jpg)

> *Рвав-рвав, собственно, на этом все.*
>
> *Ваш Смайл*
>
> *P.S. Рвав-рвав, после публикации обнаружился один тонкий момент при тестировании на других данных (несколько строк одного бренда): важен порядок проверки уровней, а именно, считать надо "снизу-вверх"*