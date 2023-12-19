---
sourcePath: ru/tracker/api-ref/concepts/entities/create-entity.md
---
# Создать сущность

Запрос позволяет создать новую сущность — [проект](../../manager/project-new.md) или [портфель проектов](../../manager/portfolio.md).

Запрос представляет унифицированный метод для создания проектов и портфелей, расширяющий возможности API [создания проектов](../projects/create-project.md).


## Формат запроса {#query}

Перед выполнением запроса [получите доступ к API](../access.md).

Чтобы создать новую сущность, используйте HTTP-запрос с методом `POST`. Параметры запроса передаются в его теле в формате JSON.

```json
POST /{{ ver }}/entities/{entityType}
Host: {{ host }}
Authorization: OAuth <OAuth-токен>
{{ org-id }}

{
   "fields": 
   {
      "summary": "<название>",
      "teamAccess": true
   }
}
```

{% include [headings](../../../_includes/tracker/api/headings.md) %}

{% cut "Ресурс" %}

**Ресурс**

Параметр | Описание | Тип данных
-------- | -------- | ----------
\<entityType> |Тип создаваемой сущности:<ul><li>project — создать проект;</li><li>portfolio — создать портфель.</li></ul>| Строка

{% endcut %} 

{% cut "Параметры запроса" %}

**Дополнительные параметры**

Параметр | Описание | Тип данных
-------- | -------- | ----------
fields |  Дополнительные поля сущности, которые будут включены в ответ. | Строка

{% endcut %}

{% cut "Параметры тела запроса" %}

Тело запроса содержит информацию, необходимую для создания новой сущности:

**Обязательные параметры**

Параметр | Описание | Тип данных
-------- | -------- | ----------
fields | Объект с настройками сущности. | Объект

**Поля объекта** `fields`

Параметр | Описание | Тип данных
-------- | -------- | ----------
summary | Название проекта (обязательное поле). | Строка
queues | Очередь (обязательное для проекта, если не указано поле `teamAccess`). | Строка
teamAccess | Доступ (обязательное для проекта, если не указано поле `queues`). | Логический

{% endcut %}

> Пример: Создать проект
> 
> - Используется HTTP-метод POST.
> - Создается проект с названием <q>Test Project</q>. 
> - К проекту подключается очередь с [ключом](../../manager/create-queue.md#key) <q>TREK</q>.
> 
> ```
> POST /v2/entities/project/ HTTP/1.1
> Host: {{ host }}
> Authorization: OAuth <OAuth-токен>
> {{ org-id }}
> 
> {
>     "fields":
>     {
>        "summary":"Test Project", 
>        "queues":"TREK"
>     }
> }
> ```

## Формат ответа {#answer}

{% list tabs %}

- Запрос выполнен успешно

   {% include [answer-201](../../../_includes/tracker/api/answer-201.md) %}

   Тело ответа содержит информацию о созданной сущности в формате JSON.
    ```json
   {
       "self": "{{ host }}/{{ ver }}/entities/project/655f3be523db2132********",
       "id": "655f3be523db2132********",
       "version": 1,
       "shortId": 6,
       "entityType": "project",
       "createdBy": { "self": "{{ host }}/{{ ver }}/users/111111117", "id": "111111117", "display": "Имя Фамилия", "cloudUid": "ajevuhegoggfk*******", "passportUid": 111111117 },
       "createdAt": "2023-11-23T11:47:49.743+0000",
       "updatedAt": "2023-11-23T11:47:49.743+0000"
   }
   ```

   {% cut "Параметры ответа" %}
    
   Параметр | Описание | Тип данных
   -------- | -------- | ----------
   self | Адрес ресурса API, который содержит информацию о сущности. | Строка
   id | Идентификатор сущности. | Строка
   version | Версия сущности. Каждое изменение параметров увеличивает номер версии. | Число
   shortId | Идентификатор проекта или портфеля. | Строка
   entityType | Тип сущности. | Строка
   createdBy | Блок с информацией о создателе сущности. | Объект
   createdAt | Дата создания сущности в формате `YYYY-MM-DDThh:mm:ss.sss±hhmm`. | Строка
   updatedAt | Дата последнего обновления сущности в формате `YYYY-MM-DDThh:mm:ss.sss±hhmm`. | Строка

   **Поля объекта** `createdBy`
    
   Параметр | Описание | Тип данных
   -------- | -------- | ----------
   self | Адрес ресурса API, который содержит информацию о создателе сущности. | Строка
   id | Идентификатор пользователя. | Число
   display | Отображаемое имя пользователя. | Строка
   cloudUid | Уникальный идентификатор пользователя в {{ org-full-name }}. | Строка
   passportUid | Уникальный идентификатор аккаунта пользователя в организации {{ ya-360 }} и Яндекс ID. | Строка

   {% endcut %}

- Запрос выполнен с ошибкой

    Если запрос не был успешно обработан, API возвращает ответ с кодом ошибки:
    
    {% include [answer-error-400](../../../_includes/tracker/api/answer-error-400.md) %}

    {% include [answer-error-401](../../../_includes/tracker/api/answer-error-401.md) %}
    
    {% include [answer-error-403](../../../_includes/tracker/api/answer-error-403.md) %}
    
    {% include [answer-error-404](../../../_includes/tracker/api/answer-error-404.md) %}
    
    {% include [answer-error-409](../../../_includes/tracker/api/answer-error-409.md) %}

{% endlist %}