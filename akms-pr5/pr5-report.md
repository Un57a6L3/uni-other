<div style="text-align: center">
<img src="../images/mirea-logo.png" alt="mirea logo" width=80 height=80>

<font size=4>МИНИСТЕРСТВО НАУКИ И ВЫСШЕГО ОБРАЗОВАНИЯ РОССИЙСКОЙ ФЕДЕРАЦИИ</font><br>
Федеральное государственное бюджетное образовательное учреждение высшего образования<br>
<b>"МИРЭА - Российский технологический университет"</b><br><br>
<font size=4><b>РТУ МИРЭА</b></font>

---
Институт информационных технологий<br>
Кафедра практической и прикладной информатики

<b>ОТЧЕТ<br>ПО ПРАКТИЧЕСКОЙ РАБОТЕ № 5</b>
<br><br>
<b>по дисциплине</b><br>
«Анализ и концептуальное моделирование систем»
<br><br>

Выполнил студент группы ИКБО-02-20
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Антонов А.Д.

Принял cтарший преподаватель
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Ахмедова Х.Г.

<br>

Практическая работа выполнена
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
«__» _______ 2022 г.

«Зачтено»
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
«__» _______ 2022 г.

<br>Москва 2022</div>

---
<div style="page-break-after: always;"></div>

# Практическая работа №5.
**Построение UML – модели системы. Диаграмма классов.**

## Цели и задачи

**Цель работы:**
изучить структуру модели проектирования, правила построения диаграммы классов.

**Задачи:**
описать сервисные функции исследуемой системы.

**Вариант: 1**
– Моделирование организации розничного бизнеса.

## Ход работы
### 1. Диаграмма классов
Построим диаграмму классов розничного предприятия:

> Рис. 1 - Диаграмма классов розничного предприятия

![class diag](../images/pr5-class-diagram.svg)

### 2. Таблицы
Заполним таблицы 1, 2 на основе полученной диаграммы в п.1:

> Таблица 1 - Описание классов диаграммы

| Название класса                | Описание                                                                                                                           |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| Сотрудник<br>(Employee)        | Базовый класс, описывающий идентификатор и вакансию сотрудника, позволяет менять и получать вакансию                               |
| Покупатель<br>(Buyer)          | Класс, описывающий идентификатор, количество денег и заказ покупателя, позволяет создавать и оплачивать заказ                      |
| Товар<br>(Goods)               | Класс, описывающий идентификатор, название, цену и количество на складе у товара, позволяет менять и получать свои поля            |
| Заказ<br>(Order)               | Класс, описывающий идентификатор, покупателя, цену, массив товаров и статус оплаты у заказа, позволяет менять и получать свои поля |
| База данных<br>(Database)      | Класс, описывающий массивы товаров, заказов и сотрудников в предприятии, позволяет менять и получать свои поля                     |
| Поставщик<br>(Supplier)        | Класс, описывающий массив имеющихся товаров, позволяет поставлять товары и создавать новые                                         |
| Кассир<br>(Cashier)            | Класс, описывающий текущий заказ и текущего покупателя у кассира, позволяет управлять заказом                                      |
| Мерчандайзер<br>(Merchandiser) | Класс, позволяющий редактировать товары через базу данных, а также заказывать и получать поставку                                  |

<br>

> Таблица 2 - Взаимодействие между классами

| Класс        | Кратность | Тип отношения      | Класс        |
| ------------ | --------- | ------------------ | ------------ |
| Сотрудник    | 1..1      | Обобщение          | Кассир       |
| Сотрудник    | 1..1      | Обобщение          | Мерчандайзер |
| Покупатель   | 1..n      | Простая ассоциация | Кассир       |
| Мерчандайзер | 1..n      | Простая ассоциация | Поставщик    |
| Мерчандайзер | n..1      | Простая ассоциация | База данных  |
| Кассир       | n..1      | Простая ассоциация | База данных  |
| Кассир       | 1..n      | Простая ассоциация | Заказ        |
| Заказ        | 1..n      | Простая ассоциация | Товар        |
| База данных  | 1..n      | Простая ассоциация | Товар        |
| База данных  | 1..n      | Простая ассоциация | Заказ        |

<div style="page-break-after: always;"></div>

## Вывод
В результате выполнения данной практической работы были изучены структура модели проектирования и правила построения диаграммы классов.

## Приложение
Диаграммы последовательности в этой работе сгенерированы с помощью кода.
Для генерации диаграммы использовался язык **PlantUML**, из написанного кода создана диаграмма в формате `.svg`.
Отчет написан в формате **Markdown** (`.md`) и экспортирован в формат `.pdf`.

Код диаграмм приведен ниже:
> Листинг 1 - Код диаграммы последовательности для приведенного варианта

```plantuml
@startuml pr5-class-diagram
!theme reddress-lightorange
skinparam BackgroundColor white

skinparam DefaultFontName "bahnschrift"
skinparam ClassFontName "bahnschrift"

skinparam DefaultFontSize 13
skinparam ClassFontSize 14

skinparam ArrowFontStyle bold

class Goods {
    id: int
    name: string
    price: int
    quantity: int

    string Name() {get; set;}
    int Price() {get; set;}
    int Quantity() {get; set;}
}

class Order {
    id: int
    buyer: Buyer
    goods: Goods[]
    price: int
    paid: bool

    Buyer Buyer() {get; set;}
    Goods[] Goods() {get; set;}

    void ApplyDiscount()
    void Pay()
}

class Buyer {
    id: int
    money: int
    order: Order

    void CreateOrder()
    bool PayOrder()
}

class Cashier {
    currentOrder: Order
    currentBuyer: Buyer

    Buyer Buyer() {get; set;}

    void CreateOrder()
    void EditOrder()
    bool PayOrder()
}

class Employee {
    id: int
    job: string

    string Job() {get; set;}
}

class Merchandiser {
    void UpdateOrderInfo()
    bool OrderGoods()
    bool UnloadGoods()
}

class Supplier {
    goods: Goods[]

    void SupplyGoods()
    bool ManufactureGoods()
}

class Database {
    goods: Goods[]
    orders: Order[]
    employees: Employee[]

    Order Orders(id) {get; set;}
    Goods Goods(id) {get; set;}
    Employee Employees(id) {get; set;}

    bool AddOrder()
    bool RemoveOrder()
    bool AddGoods()
    bool RemoveGoods()
    bool AddEmployee()
    bool RemoveEmployee()
}

left to right direction
Order "1" --> "n" Goods
Database "1" --> "n" Order
Database "1" -left-> "n" Goods
Cashier "n" --> "1" Database
Cashier "1" --> "n" Order
Buyer "1" --> "n" Cashier
Employee "1" *-- "1" Cashier
Employee "1" *-- "1" Merchandiser
Merchandiser "1" --> "n" Supplier
Merchandiser "n" --> "1" Database
@enduml
```
