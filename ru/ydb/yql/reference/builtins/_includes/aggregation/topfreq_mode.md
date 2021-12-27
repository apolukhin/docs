---
sourcePath: ru/ydb/yql/reference/yql-docs-core-2/builtins/_includes/aggregation/topfreq_mode.md
---
## TOPFREQ и MODE {#topfreq-mode}

Получение приближенного списка самых часто встречающихся значений колонки с оценкой их числа. Возвращают список структур с двумя полями:

* `Value`— найденное часто встречающееся значение;
* `Frequency` — оценка числа упоминаний в таблице.

Обязательный аргумент: само значение.

Опциональные аргументы:

1. Для `TOPFREQ` — желаемое число элементов в результате. `MODE` является алиасом к `TOPFREQ` с 1 в этом аргументе. У `TOPFREQ` по умолчанию тоже 1.
2. Число элементов в используемом буфере, что позволяет разменивать потребление памяти на точность. По умолчанию 100.

**Примеры**
``` yql
SELECT
    MODE(my_column),
    TOPFREQ(my_column, 5, 1000)
FROM my_table;
```