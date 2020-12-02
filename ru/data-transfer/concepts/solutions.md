# Какие задачи решает сервис

Сервис {{ data-transfer-name }} решает различные прикладные задачи по миграции баз данных.

Для всех задач в качестве источника могут выступать типы баз данных, развернутых:

* локально (On-premise);
* в других облаках;
* в сервисе [{{ compute-full-name }}](https://cloud.yandex.ru/services/compute);
* в сервисах [{{ mmy-full-name }}](https://cloud.yandex.ru/services/managed-mysql) и [{{ mpg-full-name }}](https://cloud.yandex.ru/services/managed-postgresql).

## Тестирование {{ yandex-cloud }} {#testing}

Тестируйте работу с сервисами {{ mmy-full-name }} и {{ mpg-full-name }} на ваших реальных данных. С помощью {{ data-transfer-name }} вы можете легко перенести свои данные в эти сервисы и ознакомиться с их возможностями.

Вы также можете запустить свое приложение и подключить к нему БД из сервисов {{ mmy-short-name }} или {{ mpg-short-name }}.

## Миграция баз данных в {{ yandex-cloud }} {#migration}

Перенесите свои данные в {{ yandex-cloud }} с помощью сервиса {{ data-transfer-name }}. При этом исходная (источник) и целевая (приемник) базы данных должны быть одинаковы, а структуры схем, типы данных и коды совместимы.

## Сценарий аварийного восстановления {#migration}

Используйте {{ data-transfer-name }} для миграции данных из {{ yandex-cloud }} в локальную БД. На вашем сервере всегда будет актуальная копия данных.

## Организация процесса разработки и разделение нагрузки {#development}

Воспользуйтесь сервисом {{ data-transfer-name }} для разделения различных сред разработки.

Например, разработчики, тестировщики или аналитики вашего продукта используют инфраструктуру {{ yandex-cloud }} для своих задач. Вы можете быстро организовать окружение для нового участника, а за наличие в нем актуальной копии данных из продуктового окружения будет отвечать сервис {{ data-transfer-name }}.

Схема работает и в обратном направлении, когда ваша актуальная стабильная версия сервиса базируется в {{ yandex-cloud }}, а для организации рабочего процесса необходимо иметь реплику данных в локальных базах. При этом продакшн БД не будет испытывать лишнюю нагрузку.

## Разделение и объединение баз данных {#separation}

Разделите единую базу данных на несколько отдельных. В каждую новую БД вы можете перенести разный набор таблиц исходной базы.

Объедините несколько баз данных в одну. Например, при миграции в {{ yandex-cloud }} вы можете собрать свои данные в единую БД в одном из сервисов управляемых баз данных. Объединять можно только однородные базы данных.