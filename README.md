# Библиоткека Spider
Библиотека создана для простых программ на Arduino с использованием [Multiservo shield](https://github.com/amperka/Multiservo) для управления одновременно 18-тю сервоприводами которые являются частями ног робота. Рассчитано что у робота есть 6 ног с 3-мя степенями свободы(То есть за движение каждой ноги отвечают 3 сервопривода).

## Начало работы
Библиотека рассчитана на Multiservo shield и основывается на их библиотеке. Поэтому для работы данной библиотеки необходимо предварительно установить библиотеку Multiservo. 

Добавление библиотеки можно сделать следующим образом предварительно скачав их в как архив

![Rus](https://github.com/Antrismus/Spider/blob/master/Illustration/Rus.png)

## Библиоткека
В библиотеке есть два класса, первый это Leg для характеристики и управление каждой ноги отдельно и второй класс Spider который соответственно управляет пауком в целом.

### Leg
```C++
#include <Leg.h>
```
Класс Leg, как уже говорилось ранее класс создан для управления ногой робота. Нога должна складываться с трех моторов (Бедро – верхний сервопривод, Колено – средний сервопривод, Ступня – нижний сервопривод)

#### Конструктор
1. Пустая нога
2. Инициалиизация ноги при создании

```C++
#include <Leg.h>

void setup() {
  Leg a();
  Leg b(15, 16, 17, 90, 130, 115, 'r');
}
```

#### Методы
1.	setupStaticAngle (Установить стандартные углы поворота для ноги)
```C++
#include <Leg.h>

void setup() {
  Leg b(15, 16, 17, 90, 130, 115, 'r');
  b.setupStaticAngle(90, 130, 115);
}
```
2.	setupSide (Устанавливает сторону ноги)
```C++
#include <Leg.h>

void setup() {
  Leg b(15, 16, 17, 90, 130, 115, 'r');
  b.setupSide('l');
}
```
3.	moving (Ставит ногу в определенное положение с помещу структуры Angle) 
Структура Angle состоит из трех углов соответственно по углу на каждый сервопривод
```C++
#include <Leg.h>

void setup() {
  Leg b(15, 16, 17, 90, 130, 115, 'r');
  // const Angle LEG_UP = {1, 60, 70}; - Стандартная константа
  b.moving(LEG_UP);
  b.moving({1, 60, 70});
}
```
4.	getCurentAngle – возвращает угл в котором находиться нога в данны момент
5.	getStaticAngle – возвращает стандартные углы для ноги
