# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнила:
- Новикова Мария Сергеевна
- РИ220935

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.

## Цель работы
Разработать оптимальный баланс для десяти уровней игры Dragon Picker.

## Задание 1
### Предложите вариант изменения найденных переменных для 10 уровней в игре. Визуализируйте изменение уровня сложности в таблице. 

Ход работы: 

- Переменные, влияющие на движение дракона на сцене: Speed, ChanceDirection, LeftRightDistance
- Переменные, влияющие на сбрасывание яиц: TimeBetweenEgg

1. Изучив и проанализировав данные и занчения этих переменных в файлах игры(0-1 сцена), я составила в таблице значения этих переменных для 10 сцен с возрастанием сложности по своему усмотрению. 

![image](https://github.com/kofuru/readme/assets/127126154/f6b3cf14-858f-4bef-8b3b-bbe1f741d62d)




## Задание 2
### Создайте 10 сцен на Unity с изменяющимся уровнем сложности.

Решение данного задания находится по ссылке: 
[https://github.com/kofuru/DragonPicker/tree/main](https://github.com/kofuru/DragonPicker/tree/main)

## Задание 3
### Решение в 80+ баллов должно заполнять google-таблицу данными из Python. В Python данные также должны быть визуализированы.
![image](https://github.com/kofuru/readme/assets/127126154/336b5314-1ea4-472a-994a-fade214e6a2b)

```
import gspread
import numpy as np
gc = gspread.service_account(filename='unitydatascience-403720-1000ece0e366.json')
sh = gc.open("UnityWorkshop3")
speed = 4.00
leftRightDistant = 10.00
chanceDirection = 0.01
timeBetweenEgg = 2.00
i = 0
end = 8
while i <= end:
    tempRand = np.random.randint(-100, 100, 3) 
    i += 1
    if i == 0:
        continue
    else:
        sh.sheet1.update(('A' + str(i+1)), i)
        sh.sheet1.update(('B' + str(i+2)), speed+2.4*i+(tempRand[0]/1000))
        sh.sheet1.update(('C' + str(i+2)), leftRightDistant+0.3*i+(tempRand[2]/1000))
        sh.sheet1.update(('D' + str(i+2)), chanceDirection+0.007*i)
        sh.sheet1.update(('E' + str(i+2)), timeBetweenEgg-0.2*i+(tempRand[1]/1000))
        print('st')

```
![image](https://github.com/kofuru/readme/assets/127126154/13f55d0f-b8ae-494c-a39c-e1701569cfa6)

## Выводы

В ходе лабораторной работы я построила экономическую модель игры с использованием выбранного игрового ресурса. С помощью скрипта на Python выгрузила данные из Google sheets в Unity используя их в работе с звуковыми эффектами. Изменила условия, при которых вопроизводился тот или иной звук в зависимости от значения из Google sheets. 
## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
