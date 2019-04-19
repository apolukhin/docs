---
editable: false
---

# Правила тарификации для [!KEYREF MG]

## Из чего складывается стоимость использования [!KEYREF mmg-short-name] {#rules}

Расчет стоимости использования [!KEYREF mmg-name] учитывает:

* тип и объем хранилища (дискового пространства);

* [класс хостов](concepts/instance-types.md), выбранный для кластера;

* количество хостов БД в кластерах;

* настройки и количество резервных копий;

* объем исходящего трафика.


[!INCLUDE [pricing-gb-size](../_includes/pricing-gb-size.md)]

### Использование хостов БД {#rules-hosts-uptime}

Стоимость начисляется за каждый час работы хоста в соответствии с его классом. Точные характеристики классов приведены в разделе [[!TITLE]](concepts/instance-types.md).

Минимальная единица тарификации — час (например, стоимость 1,5 часов работы хоста равна стоимости 2 часов). Время, когда хост [!KEYREF MG] не может выполнять свои основные функции, не тарифицируется.

### Использование дискового пространства {#rules-storage}

Оплачивается:

* Объем хранилища, выделенный для кластеров БД.

    * Хранилище на быстрых локальных дисках (NVMe) можно заказывать только для кластеров более чем с 3 хостами, с шагом 100 ГБ.


* Объем, занимаемый резервными копиями баз данных сверх заданного хранилища для кластера.

    * Резервные копии хранятся бесплатно пока сумма размера БД и всех резервных копий остается меньше выбранного объема хранилища.

    * При автоматическом резервном копировании [!KEYREF mmg-short-name] не создает новую копию, а сохраняет изменения БД по сравнению с предыдущей копией. Поэтому потребление хранилища автоматическими резервными копиями растет только пропорционально объему изменений.

    * Количество хостов кластера не влияет на объем хранилища и, соответственно, на бесплатный объем резервных копий.



Цена указывается за 1 месяц использования.  Минимальная единица тарификации — ГБ в час (например, стоимость хранения 1 ГБ в течение 1,5 часов равна стоимости хранения в течение 2 часов).

## Цены {#prices}

### Хосты {#prices-hosts}

---

**[!TAB За месяц работы хоста]**

Класс хостов | Цена за месяц, без НДС | Цена за месяц, вкл. НДС 
----- | ----- | ----- | -----
| **Intel Broadwell** |  |
[!KEYREF b1.nano]| 646 ₽ | 775 ₽
[!KEYREF b1.micro] | 948 ₽ | 1 138 ₽
[!KEYREF b1.medium] | 1 770 ₽ | 2 124 ₽
[!KEYREF s1.nano]| 1 800 ₽ | 2 160 ₽
[!KEYREF s1.micro] | 3 606 ₽ | 4 327 ₽
[!KEYREF s1.small] | 7 206 ₽ | 8 647 ₽
[!KEYREF s1.medium] | 14 418 ₽ | 17 302 ₽
[!KEYREF s1.large] | 28 830 ₽ | 34 597 ₽
[!KEYREF s1.xlarge] | 57 667 ₽ | 69 201 ₽
**Intel Cascade Lake** | | 
[!KEYREF b2.nano]| 646 ₽ | 775 ₽
[!KEYREF b2.micro] | 948 ₽ | 1 138 ₽
[!KEYREF b2.medium] | 1 770 ₽ | 2 124 ₽
[!KEYREF s2.micro] | 3 606 ₽ | 4 327 ₽
[!KEYREF s2.small] | 7 206 ₽ | 8 647 ₽
[!KEYREF s2.medium] | 14 418 ₽ | 17 302 ₽
[!KEYREF s2.large] | 21 746 ₽ | 26 095 ₽
[!KEYREF s2.xlarge] | 28 831 ₽ | 34 597 ₽
[!KEYREF s2.2xlarge] | 43 493 ₽ | 52 192 ₽
[!KEYREF s2.3xlarge] | 57 667 ₽ | 69 201 ₽
[!KEYREF s2.4xlarge]| 72 488 ₽ | 86 986 ₽
[!KEYREF s2.5xlarge]| 86 985 ₽ | 104 382 ₽

**[!TAB За 1 час работы хоста]**

Класс хостов | Цена за час, без НДС | Цена за час, вкл. НДС 
----- | ----- | ----- | -----
| **Intel Broadwell** |  |
[!KEYREF b1.nano]| 0,8975 ₽ | 1,0770 ₽
[!KEYREF b1.micro] | 1,3167 ₽ | 1,5800 ₽
[!KEYREF b1.medium] | 2,4583 ₽ | 2,9500 ₽
[!KEYREF s1.nano] | 2,5000 ₽ | 3,0000 ₽ | 
[!KEYREF s1.micro] | 5,0085 ₽ | 6,0102 ₽ | 
[!KEYREF s1.small] | 10,0085 ₽ | 12,0102 ₽ | 
[!KEYREF s1.medium] | 20,0254 ₽ | 24,0305 ₽ | 
[!KEYREF s1.large] | 40,0424 ₽ | 48,0508 ₽ | 
[!KEYREF s1.xlarge] | 80,0932 ₽ | 96,1119 ₽ 
**Intel Cascade Lake** | | 
[!KEYREF b2.nano]| 0,8975 ₽ | 1,0770 ₽
[!KEYREF b2.small] | 1,3167 ₽ | 1,5800 ₽
[!KEYREF b2.medium] | 2,4583 ₽ | 2,9500 ₽
[!KEYREF s2.micro] | 5.0085 ₽ | 6.0102 ₽
[!KEYREF s2.small] | 10.0085 ₽ | 12.0102 ₽
[!KEYREF s2.medium] | 20.0254 ₽ | 24.0305 ₽
[!KEYREF s2.large] | 30.2030 ₽ | 36.2436 ₽
[!KEYREF s2.xlarge] | 40.0424 ₽ | 48.0508 ₽
[!KEYREF s2.2xlarge] | 60.4070 ₽ | 72.4884 ₽
[!KEYREF s2.3xlarge] | 80.0932 ₽ | 96.1119 ₽
[!KEYREF s2.4xlarge]| 100.6780 ₽ | 120.8136 ₽
[!KEYREF s2.5xlarge]| 120.8130 ₽ | 144.9756 ₽

---

### Хранилище и резервные копии {#prices-storage}

Услуга | Цена за ГБ в месяц, без НДС | Цена за ГБ в месяц, вкл. НДС 
----- | ----- | -----
Стандартное сетевое хранилище | 1,9068 ₽ | 2,2881 ₽ | 
Быстрое сетевое хранилище | 6,7797 ₽ | 8,1356 ₽ | 
Быстрое локальное хранилище | 6,7797 ₽ | 8,1356 ₽ | 
Резервные копии сверх размера хранилища | 2,1186 ₽ | 2,5424 ₽ 

### Исходящий трафик {#prices-traffic}

[!INCLUDE-NOTITLE [pricing-egress-traffic](../_includes/pricing/pricing-egress-traffic.md)]