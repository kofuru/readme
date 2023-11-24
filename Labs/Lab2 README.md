# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнила:
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
Разобраться в передачи данных в Google sheets и передать данные из Google sheets в Unity с помощью Python

## Задание 1
### Выберите одну из компьютерных игр, приведите скриншот её геймплея и краткое описание концепта игры. Выберите одну из игровых переменных в игре, опишите её роль в игре, условия изменения / появления и диапазон допустимых значений. Постройте схему экономической модели в игре и укажите место выбранного ресурса в ней.

Ход работы: 

1. Выбрать одну из компьютерных игр, привести скриншот её геймплея и краткое описание концепта игры.
    Мой выбар пал на Honkai: Star Rail. 

![image](https://github.com/kofuru/readme/assets/127126154/ef7fa948-0f74-4fb3-9ef8-f4f57e4744b1)

Концепт игры простой. Игра с закрытым миром (имеющим небольшие элементы открытого мира ), ограниченными загадками, сундуками и исследованиями подземелий, с упором на пошаговые стратегические бои. Можно изучить различные стратегии с учётом пути или эелемента персонажа и противника.

2. Игровая переменная: Неугасаемый пепел. За данный ресурс можно купитьь в магазине нужные игровые ресурсы. Получить её можно за использование События Прыжка (событие, благодаря которому можно получить нового персонажа, новое оружие, неугасаемый пепел и неугасаемый звездный свет). Чтобы воспользоваться Событием нужно потратить "прыжок", его можно использовать как в чистом виде, так и купить его с помощью 160 звездного нефрита (другая игровая валюта). ПОсле использования, если вы получаете повторный 3* предмет в событии, вы получаете Неугасаемый пепел.  
    
![image](https://github.com/kofuru/readme/assets/127126154/8ea8714c-b5cc-4e3b-a03a-8efdfdeceb11)


## Задание 2
### С помощью скрипта на языке Python заполнить google-таблицу данными, описывающими выбранную игровую переменную в выбранной игре. Средствами google-sheets визуализируйте данные в google-таблице для наглядного представления выбранной игровой величины.

1. Для этого задания использую код написанный по 2 воркшопу. Поскольку игровой ресурс не имеет ограничений, то ориентируемся на самый дешевый предмет в магазине. Самый дешевый предмет стоит 4 Неугасаемого пепла, поэтому изменяем значение в коде. 
![image](https://github.com/kofuru/readme/assets/127126154/e3c512c8-b652-4d71-82cf-ff2552b17010)

2. Сверим полученные данные с выгрузкой в гугл таблицы.

![image](https://github.com/kofuru/readme/assets/127126154/66519a43-0fe0-44b9-b542-882b7ad655ae)

3. Визуализируем данные с помозью инструментов в Google sheets

![image](https://github.com/kofuru/readme/assets/127126154/b9b09dd0-0125-4870-9b10-a4a949ea61b2)

## Задание 3
### Настроить на сцене Unity воспроизведение звуковых файлов, описывающих динамику изменения выбранной переменной. 
1. Код для воспроизведения звуков в Unity на C#
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Networking;
using SimpleJSON;

public class NewBehaviourScript : MonoBehaviour
{
    public AudioClip goodSpeak;
    public AudioClip normalSpeak;
    public AudioClip badSpeak;
    private AudioSource selectAudio;
    private Dictionary<string, float> dataSet = new Dictionary<string, float>();
    private bool statusStart = false;
    private int i = 1;

    void Start()
    {
        StartCoroutine(GoogleSheets());
    }

    // Update is called once per frame
    void Update()
    {
        if (dataSet.Count == 0) return;

        if (dataSet["Mon_" + i.ToString()] > 500 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioGood());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] > 200 & dataSet["Mon_" + i.ToString()] < 500 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioNormal());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] <= 200 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioBad());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }
    }

    IEnumerator GoogleSheets()
    {
        UnityWebRequest curentResp = UnityWebRequest.Get("https://docs.google.com/spreadsheets/d/1TmAMoCoYAgXTeppaX8ySkNvZ16edTFRV_rwBgNYcEKM/edit?usp=sharing");
        yield return curentResp.SendWebRequest();
        string rawResp = curentResp.downloadHandler.text;
        var rawJson = JSON.Parse(rawResp);
        foreach (var itemRawJson in rawJson["values"])
        {
            var parseJson = JSON.Parse(itemRawJson.ToString());
            var selectRow = parseJson[0].AsStringList;
            dataSet.Add(("Mon_" + selectRow[0]), float.Parse(selectRow[2]));
        }
    }

    IEnumerator PlaySelectAudioGood()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = goodSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioNormal()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = normalSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioBad()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = badSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(4);
        statusStart = false;
        i++;
    }
}
```

- Добавила скрипт и звуковые файлы в Assets 

![image](https://github.com/kofuru/readme/assets/127126154/62703d2d-6e0d-47b3-b5a0-b7e6ee4f53cc)

![image](https://github.com/kofuru/readme/assets/127126154/f82d2548-679f-4040-9d78-952d4c4fc3a1)

- Подключила к объетку скрипт с измененными условиями и добавила звуковые файлы 
![image](https://github.com/kofuru/readme/assets/127126154/f61f05d3-2742-4f57-8476-1d1aa730b8ab)

-При запуске проекта исходя из значений полученных из Google sheeys вопроизводились нужные аудио. 

## Выводы

В ходе лабораторной работы я построила экономическую модель игры с использованием выбранного игрового ресурса. С помощью скрипта на Python выгрузила данные из Google sheets в Unity используя их в работе с звуковыми эффектами. Изменила условия, при которых вопроизводился тот или иной звук в зависимости от значения из Google sheets. 
## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
