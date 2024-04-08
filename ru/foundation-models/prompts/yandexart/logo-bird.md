# Логотип с птицей

## Параметры запроса {#params}

* **Промт**: Красивая птичка, иконка, в стиле векторной графики, в современном плоском стиле, svg.

* **Зерно**: `1`

* **Результат**:

![logo-bird](../../../_assets/yandexgpt/logo-bird.jpeg)

## Структура запроса {#structure}

```json
{
  "modelUri": "art://<идентификатор_каталога>/yandex-art/latest",
  "generationOptions": {
    "seed": 1
  },
  "messages": [
    {
      "weight": 1,
      "text": "красивая птичка, иконка, в стиле векторной графики, в современном плоском стиле, svg"
    }
  ]
}
```

Где `<идентификатор_каталога>` — [идентификатор каталога](../../../resource-manager/operations/folder/get-id.md) {{ yandex-cloud }}, у которого есть доступ к сервису {{ yagpt-name }}.

{% include [prompt-structure](../../../_includes/yandexart/prompt-structure.md) %}

## Получение результата {#result}

{% include [prompt-result](../../../_includes/yandexart/prompt-result.md) %}