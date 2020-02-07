+++
title = "Cronbox vs Zabbix, Prometheus и т.д."
date = 2020-01-22

[taxonomies]
tags = ["cronbox", "мониторинг"]
categories = ["cronbox", "мониторинг"]
+++

## С чего все началось

Проект Cronbox появился из-за необходимости простого мониторинга для cron-задач.
На момент написания этой статьи я работаю IT-инженером (operations\devops), мы много лет верны Zabbix.
У нас нет микросервисов, мы работаем с монолитами. Нам очень нравится Zabbix и он покрывает 95% наших потребностей 
в мониторинге.

Помимо администрирования (operations) я много пишу кода как по работе так и вне. Для своих side-проектов я хотел
использовать Zabbix, но для небольших объемов это оказалось трудоемким как по деньгам так и по времени.

## Мониторинг как услуга

Любое решение, независимо от того насколько вы с ним знакомы, требует поддержки. Поддержка включает в себя:

**1. Личное время**  
  Время на установку, настройку и регулярные обновления.

**2. Деньги**  
  Промышленные системы уровня Zabbix или Prometheus требуют выделенного сервера, а это дополнительные затраты на аренду и поддержку.

**3. Периодические наблюдение**  
   Как бы это не было смешно, но и мониторинг требует мониторинга ;)

С 2017 года пошел бум на облачные сервисы. Сначала появились сервисы SaaS (Software As A Service), затем все более крупные решения: 
IaaS (Infrastructure as a Service), PaaS (Platform as a Service) и т.д. 

Cronbox предоставляет мониторинг в виде сервиса (MaaS). Когда следует использовать Cronbox:

#### 1. Вы хотите заниматься бизнесом

Вы хотите заниматься бизнесом и не хотите тратить свое время на тему мониторинга, со всеми её нюансами, 
следить за безопасностью, решать проблемы с мониторингом.

Тема мониторинга в упрощенной трактовке может быть такой - *"Добавил сервер в систему мониторинга и смотришь графики доступности"*.

На деле мониторинг это отдельная область с множеством нюансов. Часть из них:

**1. Установка**
  - Выбор системы мониторинга под ваши задачи
  - Выбор оптимальной базы данных

**2. Настройка**
  - Выбор режима сбора метрик (пассивный или активный?)
  - Настройка каналов уведомлений (как минимум двух)
  - Настройка мониторинга каналов уведомлений

**3. Резервное копирование системы мониторинга** 
  - Куда копировать? С какой периодичностью?
  - Как мониторить резервное копирование?

**4. Решение проблем с системой мониторинга**
  - В новой версии исправили прошлые ошибки, нужно обновляться
  - Исследователи безопасности нашли уязвимость, нужно обновляться

И многое другое.. ;)

#### 2. Ваши бюджеты ограничены

Промышленные системы требует выделенного сервера, а это дополнительные затраты денег.
Аренда VPS-сервера для Zabbix\Prometheus будет стоить от 1 тысячи рублей в месяц, а это как минимум 15-20 тысяч в год.

Если Zabbix будет работать и с 1ГБ оперативной памяти, то Prometheus съест 4ГБ и не поперхнется. Аренда сервера с оперативной памятью от 4ГБ это уже порядки от 2000 руб и выше.


## Резюме

Каждая бизнес-задача требует уникального подхода и соответствующего выбора инструментов для решения.

- Zabbix и Prometheus отлично решают задачи для средних и больших инфраструктур.
- Cronbox и другие облачные сервисы для мониторинга удобны для небольших и средних размеров.

Выбор решения как всегда остается за бизнесом.