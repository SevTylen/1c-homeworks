# Планы счетов и регистры бухгалерии

## Задание 1

### Описание задачи

Создать простой план счетов управленческого учета с кодами, повторяющими коды счетов РСБУ.

### Требование к результату

Конфигурация из [диплома Б](diploma-b.md), содержащая план счетов "Управленческий" с предопределенными счетами:

* 41 "Товары"
* 60 "Расчеты с поставщиками"
* 62 "Расчеты с покупателями"
* 70 "Расчеты с сотрудниками"
* 50 "Денежные средства"
* 90 "Продажи", с субсчетами:
* 90.1 "Выручка"
* 90.2 "Расходы"

### Процесс выполнения

Конфигурация из [диплома Б](diploma-b.md).

1. Добавьте подсистему "Учет".

2. Добавьте в нее план счетов "Управленческий" с длиной кода 4, с шаблоном кода счета "##.#" и автопорядком по коду.
К нему добавьте предопределенные счета:

* 41 Товары ("Товары")
* 60 РасчетыСПоставщиками ("Расчеты с поставщиками")
* 62 РасчетыСПокупателями ("Расчеты с покупателями")
* 70 РасчетыССотрудниками ("Расчеты с сотрудниками")
* 50 ДенежныеСредства ("Денежные средства")
* 90 Продажи ("Продажи"), с субсчетами:
* 90.1 Выручка ("Выручка")
* 90.2 Расходы ("Расходы")

## Задание 2

### Описание задачи

Создать регистр бухгалтерии **Управленческий** и дополнить документ **РеализацияТоваровИУслуг** движениями по нему.

### Требование к результату

Конфигурация из предыдущего задания, содержащая регистр бухгалтерии **Управленческий** с корреспонденциями и с ресурсом Сумма.

Документ **РеализацияТоваровИУслуг** должен формировать движения:

* Дт 62 - Кт 90.1 на общую сумму (аналогично движениям по регистрам накопления **Доходы** и **ВзаиморасчетыСКонтрагентами**).
* Дт 90.2 - Кт 41 на сумму списания товаров (аналогично движениям по регистрам накопления **Расходы** и **Товары**).

### Процесс выполнения

Конфигурация из предыдущего задания.

1. Добавьте регистр бухгалтерии **Управленческий** с корреспонденцией, планом счетов **Управленческий** и единственным балансовым ресурсом **Сумма** (ОпределяемыйТип.Сумма). Укажите документ **РеализацияТоваровИУслуг** как регистратор по нему.

2. В обработчик проведения документа **РеализацияТоваровИУслуг** добавьте код, который:

* Очистит движения по регистру **Управленческий**.
* Добавит движение в Дт предопределенного счета РасчетыСПокупателями и в Кт счета Выручка на общую сумму.
* Добавит движение в Дт предопределенного счета Расходы и в Кт счета Доходы на сумму списания товаров.
* Запишет движения.
