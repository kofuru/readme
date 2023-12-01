# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #4 выполнила:
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
- Реализовать перцептрон, который умеет производить вычисления в Unity и дать комментарии о корректности работы 
- Задание 2.
- Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения.
- Задание 3.
- Построить визуальную модель работы 'перцептрона' на сцене Unity.
- Выводы.

## Цель работы
Ознакомиться и реализовать персиптрон в Unity. Также визуализировать их в Google sheets

## Задание 1
### Реализовать перцептрон, который умеет производить вычисления в Unity и дать комментарии о корректности работы 
- Создала пустой обьект и прикрепила к нему файл перцептрон
![image](https://github.com/kofuru/readme/assets/127126154/c3cd7e12-1d19-4556-bdd4-2854e9118a07)

### OR - работает корректно
![image](https://github.com/kofuru/readme/assets/127126154/9ceb1887-3dc4-42c6-8974-f4e5193d81df)

### AND - работает корректно
![image](https://github.com/kofuru/readme/assets/127126154/fd6a3e39-150d-454e-a280-318915f73564)

### NAND - работает корректно
![image](https://github.com/kofuru/readme/assets/127126154/c8a45c52-031b-4249-8349-2935999a11ae)

### XOR - не корректен 
![image](https://github.com/kofuru/readme/assets/127126154/8cea4580-5711-4cfa-a275-fbe27a3235f6)
![image](https://github.com/kofuru/readme/assets/127126154/4e143590-cc85-434c-a554-7fe28a47f65c)

## Задание 2
### Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения.
![image](https://github.com/kofuru/readme/assets/127126154/ffd14fc3-b8b9-4f4b-9a84-ed6384c32946)

- Необходмое количество эпох обучения зависит от количества ошибок. Если на определенной эпохе ошибки нет, то бишь результат равен 0, то это нужная эпоха для обучения.
  
## Задание 3
### Построить визуальную модель работы 'перцептрона' на сцене Unity.

-Создаём кубы и платформу. 

![image](https://github.com/kofuru/readme/assets/127126154/328dc0b2-1f04-49ab-92cd-6c63513f1ae3)

### AND
![image](https://github.com/kofuru/readme/assets/127126154/7d4f2753-d50d-4add-a6dc-96e18d2099be)
![image](https://github.com/kofuru/readme/assets/127126154/4b605e16-5af5-4a30-9fb1-90bdd6bec888)

### OR
![image](https://github.com/kofuru/readme/assets/127126154/9522efd5-6458-4847-9396-e04f582b42c5)
![image](https://github.com/kofuru/readme/assets/127126154/8f778869-b524-49ba-a0db-e11f6fc493e6)

### XOR
![image](https://github.com/kofuru/readme/assets/127126154/fcef95ab-15f1-4b76-a12a-3f3350089352)
![image](https://github.com/kofuru/readme/assets/127126154/e3627a5a-236b-4c1e-82fe-f2990d5f7fd9)

### NAND
![image](https://github.com/kofuru/readme/assets/127126154/1e6ea555-38c2-416e-bd03-50a04000fbfb)
![image](https://github.com/kofuru/readme/assets/127126154/b7de3ffe-7f68-4c30-80e4-7aca51dd4bb3)


## Выводы

В ходе лабораторной работы я проанализировала переменные игры и вычислила их значения для усложнения 10 уровней. Затем я реализовала 10 уровней на Unity в изменении переменных в сцене. С помощью скрипта на Python из прошлых воркшопов, который я изменила под нужные условия, я выгрузила данные в Google sheets и создала диаграммы.  
## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
