+++
title = "Зачем нужен мониторинг"
description = "Почему мониторинг необходим для любого Web-проекта, независимо от его размера"
date = 2020-05-09

[taxonomies]
tags = ["monitoring", "server"]
categories = ["monitoring", "meta"]
+++

Мониторинг — это процесс наблюдения за системой. Система имеет определенное внутреннее состояние и 
периодически взаимодействует с внешним миром. 

Системой может быть сайт, Интернет-магазин или любое другое приложение.
Для Интернет-магазина внутреннее состояние системы — это заказы, товары, данные об оплате, а взаимодействие 
с внешним миром — обработка платежей с банками (эквайринг).   

Процесс наблюдения может быть ручным, полу или полностью автоматическим:
- ручной — открываем сайт и видим что он успешно загрузился. 
- полуавтоматический — смотрим на градусник и принимаем решение какую одежду одеть.
- автоматический — система уведомляет нас о сбоях или авариях.

**Автоматический мониторинг необходим для проектов любого размера.**

Для примера возьмем некий магазин, который продает детские игрушки через Интернет. 
Заказы принимаются через сайт, круглосуточно. Операторы обрабатывает заявки с 9:00 до 17:00, каждый день. 
Вечером, на сервере, стартует задача для создания резервной копии базы данных и файлов сайта.

В один прекрасный день, по внешним обстоятельствам (обновление операционной системы, ошибка в приложении) 
механизм архивации перестал работать. Об аварии никто не узнал, т.к. мониторинг не был подключен.  

Владелец магазина решил обновить версию программного обеспечения 
магазина, чтобы добавить возможность интеграции с Facebook. 
Обновление прошло с ошибкой, потребовалось откатить файлы и базу данных до состояния вчерашнего дня. 
Так как механизм архивирования сломался месяц назад, то и данные в архиве 
остались месячной давности. При этом, за прошедший месяц было добавлено 1000 товарных позиций, обновлена верстка сайта, 
опубликованы 30 новостей и 5 акций.

Владелец магазина предстает перед выбором: отказаться от месяца работ над сайтом или пытаться победить ошибку обновления
текущей версии сайта. Независимо от выбранного варианта бизнес понесет убытки.

Если бы владелец подключил систему мониторинга, то об аварии узнали заблаговременно.
 
**Мониторинг должен быть независим от той системы за которой он наблюдает.**

Второй пример — агентство новостей. Каждый вечер агентство рассылает своим подписчикам письмо с новостями за день.
В рассылке содержатся ссылки на сайт агентства и партнерские сайты. Механизм рассылки реализован в виде задачи 
на сервере, которая запускается каждый день в 17:00. 

По внешним обстоятельствам изменился пароль для учетной записи 
на почтовом сервере. В задаче рассылки был встроен механизм отправки письма на почту о состоянии задачи. 
Сотрудница, которая проверяла подобные письма, ушла на две недели в отпуск. Её почту переадресовали коллеге, но та 
не была проинформирована о необходимости следить за мониторингом. Главный редактор спокоен и уверен 
что почтовая рассылка работает.

Наступает праздничный день, на который очень рассчитывают рекламодатели. Почтовая рассылка не приходит.
Один из партнеров пишет гневное письмо, про то что их реклама не публикуется, рассылки нет. 
В итоге, агентство получает урон репутации и потерю прибыли. Полуавтоматический мониторинг на базе людей дал сбой.

Если бы компания подключила внешнюю и независимую систему мониторинга, то проблему рассылки удалось бы устранить 
в кратчайшие сроки.

#### Мониторинг как сервис

Мы предлагаем сервис для непрерывного автоматического мониторинга серверных задач.

Вам достаточно [подключить](https://docs.cronbox.ru/getting-started/) задачи к системе мониторинга и 
сервис будет следить за их выполнением. Наш сервис уведомит вас по почте и\или в Telegram в случаях когда:
- Задача отработала успешно.
- Задача не запустилась или отработала с ошибкой.
- Задача работала дольше чем обычно. 