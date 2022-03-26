<div style="text-align: center">
<img src="../images/mirea-logo.png" alt="mirea logo" width=80 height=80>

<font size=4>МИНИСТЕРСТВО НАУКИ И ВЫСШЕГО ОБРАЗОВАНИЯ РОССИЙСКОЙ ФЕДЕРАЦИИ</font><br>
Федеральное государственное бюджетное образовательное учреждение высшего образования<br>
<b>"МИРЭА - Российский технологический университет"</b><br><br>
<font size=4><b>РТУ МИРЭА</b></font>

---
Институт информационных технологий<br>
Кафедра практической и прикладной информатики

<b>ОТЧЕТ<br>ПО ПРАКТИЧЕСКОЙ РАБОТЕ № 3</b>
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

# Практическая работа №3.
**Построение UML – модели системы. Диаграмма классов анализа.**

Содержание:
- [Практическая работа №3.](#практическая-работа-3)
  - [Цели и задачи:](#цели-и-задачи)
  - [Ход работы:](#ход-работы)
  - [Вывод:](#вывод)
  - [Приложение:](#приложение)

## Цели и задачи:

**Цель работы:**
изучить структуру иерархии классов системы.

**Задачи:**
научиться выстраивать структуру основных элементов диаграммы классов анализа с определением видов классов и типов отношений.

**Вариант: 1**
– Моделирование организации продаж новых автомобилей в автосалоне.

## Ход работы:
Построить диаграмму классов анализа рассматриваемой системы с учетом индивидуального варианта (Рис. 1):

![diagram](../images/pr3-class-diagram.svg)

> Рис. 1 - Построенная диаграмма классов.

В верхней части диаграммы абстрактно выделены основные функции автосалона - учёт и продажа автомобилей, поиск и привлечение клиентов и т.д.
В нижней части диаграммы описана концептуальная система базы данных автосалона.

## Вывод:
В результате данной практической работы были изучены элементы структуры иерархии классов диаграммы UML. Было выполнено задание в соответствии с индивидуальным вариантом.

<div style="page-break-after: always;"></div>

## Приложение:
Диаграмма и этот вариант отчета сгенерированы с помощью кода.
Для генерации диаграммы использовался язык PlantUML, из написанного кода создана диаграмма в формате svg.
Этот вариант отчета написан в формате Markdown и экспортирован в формат pdf.

Код диаграммы на языке PlantUML приведен ниже:
```plantuml
@startuml PR3

!$ent = {"letter": "E", "color": "#ff1700"}
!$bnd = {"letter": "B", "color": "#ffa600"}
!$ctr = {"letter": "C", "color": "#4d6910"}

!theme reddress-lightred
hide members

skinparam BackgroundColor white
skinparam DefaultFontName "jetbrains mono"
skinparam ClassFontName "jetbrains mono"

legend left
Типы классов:
<color:$ent.color>**( $ent.letter )**</color> - класс сущности
<color:$bnd.color>**( $bnd.letter )**</color> - граничный класс
<color:$ctr.color>**( $ctr.letter )**</color> - управляющий класс
end legend

namespace main {
    class dealership as "Автосалон" << ($ent.letter, $ent.color) >>

    class cars as "Автомобили" << ($ent.letter, $ent.color) >>
    class salesdept as "Отдел\nпродаж" << ($ent.letter, $ent.color) >>
    class manager as "Менеджер" << ($ent.letter, $ent.color) >>

    class caracc as "Учет\nавтомобилей" << ($bnd.letter, $bnd.color) >>
    class carbuy as "Закупка\nавтомобилей" << ($bnd.letter, $bnd.color) >>
    class carsell as "Продажа\nавтомобилей" << ($bnd.letter, $bnd.color) >>
    class carinfo as "Представление\nинформации" << ($bnd.letter, $bnd.color) >>

    class specs as "Характеристики" << ($ent.letter, $ent.color) >>
    class price as "Цена" << ($ent.letter, $ent.color) >>

    class clientsearch as "Поиск\nклиентов" << ($ctr.letter, $ctr.color) >>
    class clientattract as "Привлечение\nклиентов" << ($bnd.letter, $bnd.color) >>

    class reserve as "Осуществление\nбронирования" << ($ctr.letter, $ctr.color) >>
}

namespace database {
    class basedialog as "Диалоговое\nокно БД" << ($bnd.letter, $bnd.color) >>

    class dwinfoclient as "Диалоговое окно\nданных клиента" << ($bnd.letter, $bnd.color) >>
    class dwinfocar as "Диалоговое окно\nинформации\nоб автомобиле" << ($bnd.letter, $bnd.color) >>
    class dwpaystatus as "Диалоговое окно\nстатуса оплаты" << ($bnd.letter, $bnd.color) >>

    class controlpanel as "Панель\nуправления" << ($bnd.letter, $bnd.color) >>
    class tablist as "Набор\nвкладок" << ($bnd.letter, $bnd.color) >>
    class appaccsystem as "Система\nучета заявок" << ($bnd.letter, $bnd.color) >>

    class appclients as "Заявки\nклиентов" << ($bnd.letter, $bnd.color) >>
    class nodetree as "Дерево\nузлов" << ($bnd.letter, $bnd.color) >>
}

main.dealership o-- main.cars
main.dealership o-- main.salesdept
main.dealership o-- main.manager

left to right direction
main.manager *-- main.caracc
main.manager *-- main.carbuy
main.manager *-- main.carsell
main.manager *-- main.carinfo

main.carinfo --> main.specs
main.carinfo --> main.price

main.salesdept ..> main.clientsearch
main.salesdept *-- main.clientattract

main.reserve o-- main.manager
main.reserve ..> database.basedialog

database.basedialog <|-- database.dwinfoclient
database.basedialog <|-- database.dwinfocar
database.basedialog <|-- database.dwpaystatus

database.basedialog *-- database.controlpanel
database.basedialog *-- database.tablist
database.basedialog *-- database.appaccsystem

database.appaccsystem *-- database.appclients
database.appaccsystem *-- database.nodetree
@enduml

```
