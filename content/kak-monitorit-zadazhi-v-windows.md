+++
title = "Как мониторить задачи из планировщика Windows"
description = "Как настроить мониторинг для планировщика задач Windows."
date = 2020-06-04

[taxonomies]
tags = ["scheduler"]
categories = ["tutorial", "windows"]
+++

Несмотря на то что наш проект называется [Cronbox](https://cronbox.ru) и 
первоначально он был создан для мониторинга cron-задач в Linux, вы можете пользоваться сервисом и для Windows-серверов.

Планировщик задач для Windows умеет делать всё тоже что и `cron` и кое что дополнительно. Например, поддерживает часовые
пояса.

![alt text](/images/windows-scheduler.png "Планировщик задач Windows")

Для примера интегрируем задачу резервного копирования с Cronbox.

#### 1. Копируем ссылку монитора

После [создания монитора](https://docs.cronbox.ru/getting-started/) мы получим уникальную ссылку вида:

![alt text](/images/windows-scheduler/monitor-page-url.png "Страница монитора")

Копируем её в блокнот, она ещё пригодится.

#### 2. Настраиваем задачу в планировщике

Настроим отправку HTTP-запроса к монитору после завершения выполнения задачи. 
Для отправки можно использовать утилиту `curl` для Windows, её можно [скачать с официального сайта](https://curl.haxx.se/windows/). 

Открываем «Планировщик заданий», затем свойства («Properties») задачи для резервного копирования:

![alt text](/images/windows-scheduler/edit-scheduler-task.png "Редактирование задачи в планировщике Windows")

На вкладке «Action» (в русской версии «Действие») нажимаем «Edit».

![alt text](/images/windows-scheduler/task-edit-action.png "Редактирование задачи")

К команде добавляем отправку:

![alt text](/images/windows-scheduler/windows-task-append-curl.png "Добавляем curl-запрос")

Команда будет выглядеть подобным образом:

```shell script
c:\backups\start.cmd && curl -fsS --retry 3 https://cronbox.ru/ping/39879ead-7a97-455f-9c95-4dbf08d16140
```

Сохраняем изменения.

Задача подключена к монитору. Теперь если задача выполнится успешно, то будет отправлен запрос к монитору в Cronbox.

