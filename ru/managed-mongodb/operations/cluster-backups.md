# Управление резервными копиями

Вы можете создавать резервные копии и восстанавливать кластеры из имеющихся резервных копий.


## Восстановить кластер из резервной копии {#restore}

Восстанавливая кластер из резервной копии, вы создаете новый кластер с данными из резервной копии. Если в каталоге не хватает [ресурсов](../concepts/limits.md) для создания такого кластера, восстановиться из резервной копии не получится.

Для нового кластера необходимо задать все параметры, обязательные при создании, кроме типа кластера (резервную копию [!KEYREF MG] не получится восстановить как кластер [!KEYREF PG]).

---

**[!TAB Консоль управления]**

1. Перейдите на страницу каталога и нажмите плитку **[!KEYREF mmg-name]**.

2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.

3. Нажмите значок ![image](../../_assets/dots.svg) для нужной резервной копии, затем нажмите **Восстановить кластер**.

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

Чтобы восстановить кластер из резервной копии:

1. Посмотрите описание команды CLI для восстановления кластера [!KEYREF MG]:

    ```
    $ [!KEYREF yc-mdb-mg] cluster restore --help
    ```

2. Получите список доступных резервных копий [!KEYREF MG]-кластеров:

    ```
    $ [!KEYREF yc-mdb-mg] backup list
    
    +--------------------------+----------------------+----------------------+----------------------+
    |            ID            |      CREATED AT      |  SOURCE CLUSTER ID   |      STARTED AT      |
    +--------------------------+----------------------+----------------------+----------------------+
    | c9qlk4v13uq79r9cgcku:... | 2018-11-02T10:08:38Z | c9qlk4v13uq79r9cgcku | 2018-11-02T10:08:37Z |
    | ...                                                                                           |
    +--------------------------+----------------------+----------------------+----------------------+
    ```

1. Запросите создание кластера из резервной копии:

    ```
    $ [!KEYREF yc-mdb-mg] cluster restore \
         --backup-id c9q287aqv5rf11isjeql:20181113T133617 \
         --name mynewmg \
         --environment=PRODUCTION \
         --network-name default \
         --host zone-id=ru-central1-c,subnet-id=b0rcctk2rvtr8efcch63 \
         --mongod-disk-size 20 \
         --mongod-disk-type network-nvme \
         --mongod-resource-preset s1.nano
    ```

    В результате будет создан [!KEYREF MG]-кластер со следующими характеристиками:
    
    
    
    - С именем `mynewmg`.
    - В окружении `PRODUCTION`.
    - В сети `default`.
    - С одним хостом класса `s1.nano` в подсети `b0rcctk2rvtr8efcch63`, в зоне доступности `ru-central1-c`.
    - С базами данных и пользователями из резервной копии.
    - С сетевым SSD-хранилищем объемом 20 ГБ.

---


## Создать резервную копию {#create-backup}

---

**[!TAB Консоль управления]**

1. Перейдите на страницу каталога и нажмите плитку **[!KEYREF mmg-name]**.

2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.

3. Нажмите кнопку **Создать резервную копию**.

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

Чтобы создать резервную копию кластера:

1. Посмотрите описание команды CLI для создания резервной копии [!KEYREF MG]:

    ```
    $ [!KEYREF yc-mdb-mg] cluster backup --help
    ```

2. Запросите создание резервной копии, указав имя или идентификатор кластера:

    ```
    $ [!KEYREF yc-mdb-mg] cluster backup my-mg-cluster
    ```

    Имя и идентификатор кластера можно получить со [списком кластеров](cluster-list.md#list-clusters).

---


## Получить список резервных копий {#list-backups}

---

**[!TAB Консоль управления]**

1. Перейдите на страницу каталога и нажмите плитку **[!KEYREF mmg-name]**.

2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

Чтобы получить список резервных копий кластеров [!KEYREF MG], доступных в каталоге по умолчанию, выполните команду:

```
$ [!KEYREF yc-mdb-mg] backup list

+----------+----------------------+----------------------+----------------------+
|    ID    |      CREATED AT      |  SOURCE CLUSTER ID   |      STARTED AT      |
+----------+----------------------+----------------------+----------------------+
| c9qv4... | 2018-10-31T22:01:07Z | c9qv4ql6bd4hfo1cgc3o | 2018-10-31T22:01:03Z |
| c9qpm... | 2018-10-31T22:01:04Z | c9qpm90p3pcg71jm7tqf | 2018-10-31T22:01:04Z |
+----------+----------------------+----------------------+----------------------+
```

---


## Получить информацию о резервной копии {#get-backup}

---

**[!TAB Консоль управления]**

1. Перейдите на страницу каталога и нажмите плитку **[!KEYREF mmg-name]**.

2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

Чтобы получить данные о резервной копии кластера [!KEYREF MG], выполните команду:

```
$ yc [!KEYREF yc-mdb-mg] backup get <идентификатор резервной копии>
```

Идентификатор резервной копии можно получить со [списком резервных копий](#list-backups).

---

