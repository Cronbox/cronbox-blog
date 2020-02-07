+++
title = "Планировщик задач Cron"
date = 2020-01-21

[taxonomies]
tags = ["cron"]
categories = ["tutorial"]
+++

## Введение

Cron - это программа-демон, которая выполняет задания в определенное время. Такой класс программ обычно называют планировщиками задач.

В качестве задач выступают команды из оболочки операционной системы. 

Основные возможности:
- Запускать задачи в указанные даты и время
- Запускать задачи с интервалом. Например, раз в 5 минут

### Файловая структура

Cron это гибкое приложение и поэтому имеет множественные места хранения задач. Это было сделано для того чтобы:

1. Каждый пользователь мог работать только со своими задачами

2. Разделить выполнение задач тематически  
    Например, если положить скрипт в каталог `/etc/cron.daily`, то он выполнится 1 раз в сутки.
    
Тематические каталоги:

- `/etc/cron.hourly/*` — сценарии выполняющиеся каждый час
- `/etc/cron.daily/*` — сценарии выполняющиеся каждый день
- `/etc/cron.weekly/*` — сценарии выполняющиеся каждую неделю
- `/etc/cron.monthly/*` — сценарии выполняющиеся каждый месяц

В тематические каталоги помещаются готовые скрипты, расписание для скриптов не указывается. 
Если создать скрипт в каталоге `/etc/cron.hourly`, то он будет запускаться 1 раз в час. 

Если вы хотите хранить расписание в отдельном файле, то можно поместить его в каталог `/etc/cron.d`.

### Формат записи

Каждое задание для cron записывается вот в таком формате:

```
<минута> <час> <день-месяца> <месяц> <день-недели> <пользователь> <команда>
```

Если значение поля не важно, то достаточно указать знак звездочки - `*`. 
В таком случае cron будет оперировать предоставленными значениями.
Но что будет если указать для всех временных полей `*`? Команда будет запускаться раз в минуту.

В главном конфигурационном файле `/etc/crontab` добавлены подсказки:

```
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of the month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday;
# │ │ │ │ │                                   7 is also Sunday on some systems)
# │ │ │ │ │
# │ │ │ │ │
# * * * * * command to execute
```

### Примеры интервалов

Запустить скрипт для бэкапов каждый вечер в 23:00 от пользователя `backup`:

    ```
    0 23 * * * backup /scripts/backup.sh
    ```
    
Запускать скрипт каждые 15 минут:

    ```
    */15 * * * * backup /scripts/fetch.sh
    ```
    
Запускать скрипт только в выходные дни:

    ```
    */15 * * * 6-7 backup /scripts/fetch.sh
    ```
    
Запускать скрипт в 5 утра, 1го числа Января и Февраля

    ```
    5 4 1 1-2 * backup /scripts/fetch.sh
    ```

---

## Работа с задачами

### Как добавить задачу

Для примера будем запускать скрипт резервного копирования `/home/eugene/scripts/backup.sh` каждый день в 23:00.

Для этого создадим файл `/etc/cron.d/site-backup` следующего содержания:

```
0 23 * * * eugene /home/eugene/scripts/backup.sh
```

Затем рестартуем cron чтобы он перечитал свои конфигурационные файлы:

```shell script
service crond restart
```

### Как удалить задачу

Это можно сделать как минимум тремя способами:

1. Удалить файл с заданием
2. Удалить строчку из файла
3. Закомментировать строчку
    ```
    #0 23 * * * backup /scripts/backup.sh
    ```
   
Независимо от выбранного способа в конце следует перезапустить cron:

```shell script
service crond restart
```  
  
---

## Полезные ссылки

- [Другие посты из цикла про cron](/tags/cron)

- [Crontab Guru](https://crontab.guru/) - сервис для проверки временных интервалов. Вбиваешь конфигурацию задачи и узнаешь когда она будет запускаться.
