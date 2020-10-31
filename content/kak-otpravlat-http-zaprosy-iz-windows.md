+++
title = "Как отправлять HTTP-запросы в Windows"
description = "Утилиты для отправки HTTP-запросов в Windows"
date = 2020-10-31

[taxonomies]
tags = ["http", "windows", "curl", "scoop"]
categories = ["windows", "network"]
+++

![HTTP-запросы из Windows](/images/http-from-windows/requests.png "HTTP-запросы из Windows")  
  
При разработке программного обеспечения и 
при [мониторинге серверов](https://blog.cronbox.ru/kak-monitorit-zadazhi-v-windows/) порой 
необходимо отправлять HTTP-запросы. Самые популярные из них это: `POST` и `GET`.

В мире Linux/Unix/MacOS чаще всего используют утилиту `curl`, которая устанавливается одной командой. 
В Windows вы также можете установить curl.

## Способ №1 — Установка через менеджер пакетов

Самый простой и быстрый вариант — установить через менеджер пакетов [scoop](https://scoop.sh/):

```shell script
scoop install curl
```

## Способ №2 — Установка с официального сайта

1. Скачиваем архив с официального сайта [https://curl.haxx.se/windows/](https://curl.haxx.se/windows/) архив.
2. Распаковываем куда-нибудь. Например, `c:\apps\curl`. Содержимое каталога должно выглядеть подобным образом:  
    ![Содержимое директории curl](/images/http-from-windows/curl-directory.png "Содержимое директории curl")
    
3. Добавляем путь `c:\apps\curl\bin` в переменную окружения `PATH`:
    1. Открываем панель системных свойств:
        ПУСК -> Пишем "Перемен" или "Var" (для английской версии):  
        ![Как открыть редактор переменных окружения](/images/http-from-windows/start-env-vars.png "Как открыть редактор переменных окружения")
    2. Переходим в раздел работы с переменными окружения:
        ![Открываем раздел с переменными окружения](/images/http-from-windows/vars-editor1.png "Открываем раздел с переменными окружения")
    3. Находим в списке переменных окружения для пользователя переменную PATH и редактируем:
        ![Редактируем переменную PATH](/images/http-from-windows/vars-editor2.png "Редактируем переменную PATH")
    4. Добавляем новое значение `c:\apps\curl\bin`:
        ![Добавляем путь c:\\apps\\curl\\bin](/images/http-from-windows/vars-editor3.png "Добавляем путь c:\\apps\\curl\\bin")
    5. Далее нажимаем кнопки ОК пока не закроются все окна.
    
Теперь если открыть командную строку вновь, то будет доступна команда curl:

```shell script
C:\apps>curl
curl: try 'curl --help' for more information
```
        
