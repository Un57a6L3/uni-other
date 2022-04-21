# Практическая работа №7.
**Построение UML – модели системы. Диаграммы компонентов, развертывания.**

Содержание:
- [Практическая работа №7.](#практическая-работа-7)
  - [Цели и задачи](#цели-и-задачи)
  - [Ход работы](#ход-работы)
  - [Вывод](#вывод)
  - [Приложение](#приложение)

## Цели и задачи

**Цель работы:**
научиться строить модель реализации.

**Задачи:**
построить модель реализации с помощью диаграмм компонентов и развертывания с рассмотрением основных элементов и правил построения.

**Вариант: 1**
– Моделирование организации розничного бизнеса.

## Ход работы
1. Построить диаграмму компонентов розничного торгового предприятия.

> Рис. 1 - Диаграмма компонентов

![component diag](../images/pr7-component-diagram.svg)

2. Построить диаграмму развертывания розничного торгового предприятия.

> Рис. 2 - Диаграмма развертывания

![deployment diag](../images/pr7-deployment-diagram.svg)

## Вывод
В результате выполнения данной практической работы было изучено построение модели реализации.

## Приложение
Диаграммы последовательности в этой работе сгенерированы с помощью кода.
Для генерации диаграммы использовался язык **PlantUML**, из написанного кода создана диаграмма в формате `.svg`.
Отчет написан в формате **Markdown** (`.md`) и экспортирован в формат `.pdf`.

Код диаграмм приведен ниже:
> Листинг 1 - Код диаграммы ..

```plantuml
@startuml pr7-component-diagram
node "Продажа" as Selling {
    component CreateOrder [
        <<CreateOrder>>
        Компонент для
        создания заказа
    ]
    component PayOrder [
        <<PayOrder>>
        Компонент для
        оплаты заказа
    ]
    interface "Данные заказа" as OrderData1
    interface "Связь с БД" as FTP1
}

node "Управление" as Control {
    component EditGoods [
        <<EditGoods>>
        Компонент для
        редактирования
        информации
        о товарах
    ]
    component OrderGoods [
        <<OrderGoods>>
        Компонент для
        заказа товаров
        у поставщиков
    ]
    interface "Данные заказа" as OrderData2
    interface "Связь с БД" as FTP2
}

node "Учет" as AccountingNode {
    component Accounting [
        <<Accounting>>
        Компонент учета
    ]
    interface "Связь с БД" as FTP3
}

[База данных] as GoodsDB

CreateOrder .. FTP1
PayOrder .. FTP1

CreateOrder --> OrderData1
PayOrder --> OrderData1
PayOrder <-- OrderData1

EditGoods .. FTP2
OrderGoods .. FTP2
OrderGoods --> OrderData2

Accounting .. FTP3

FTP1 .. GoodsDB
FTP2 .. GoodsDB
FTP3 .. GoodsDB
@enduml
```

<br>

> Листинг 2 - Код диаграммы ..

```plantuml
@startuml pr7-deployment-diagram
node Cashpoint [
    <<Cashpoint>>
    Касса
]
node Terminal [
    <<Terminal>>
    Терминал работы с
    товарами и поставками
]
node Server [
    <<Server>>
    Сервер предприятия
]
node Network [
    <<Network>>
    Закрытая сеть
]
database BuyerDB [
    <<BuyerDB>>
    База данных
    покупателей
]
database GoodsDB [
    <<GoodsDB>>
    База данных
    товаров
]

note bottom of Cashpoint
    Кассир создает заказы
    ----
    Покупатель оплачивает
    заказы
end note

note bottom of Terminal
    Связывается с
    поставщиками
    ----
    Мерчандайзер
    редактирует товары
    ----
    Мерчандайзер
    взаимодействует
    с поставками
end note

Network -- Cashpoint
Network -- Terminal
Network -- Server
Server .. BuyerDB
Server .. GoodsDB
@enduml
```