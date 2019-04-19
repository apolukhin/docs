# Управление доступом

Пользователь Яндекс.Облака может выполнять только те операции над ресурсами, которые разрешены назначенными ему ролями. Пока у пользователя нет никаких ролей, почти все операции ему запрещены.

Чтобы разрешить доступ к ресурсам сервиса [!KEYREF mch-name] (кластеры и хосты БД, резервные копии кластеров, базы данных и их пользователи), назначьте пользователю нужные роли из приведенного ниже списка. На данный момент роль может быть назначена только на родительский ресурс (каталог или облако), роли которого наследуются вложенными ресурсами.

> [!NOTE]
>
> Подробнее о наследовании ролей читайте в разделе [[!TITLE]](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) документации сервиса [!KEYREF resmgr-full-name].

## Назначение ролей

Чтобы назначить пользователю роль:

[!INCLUDE [grant-role-console](../../_includes/grant-role-console.md)]

## Роли

Ниже перечислены все роли, которые учитываются при проверке прав доступа в сервисе [!KEYREF mch-name].

### Сервисные роли

_Сервисные роли_ — роли, дающие доступ к ресурсам определенного сервиса.

[!INCLUDE [cloud-roles](../../_includes/cloud-roles.md)]

### Примитивные роли

Примитивные роли можно назначать на любой ресурс в любом сервисе.

#### [!KEYREF roles-viewer]

Пользователь с ролью `[!KEYREF roles-viewer]` может просматривать информацию о ресурсах, например посмотреть список хостов или получить информацию о кластере БД.

#### [!KEYREF roles-editor]

Пользователь с ролью `[!KEYREF roles-editor]` может управлять любыми ресурсами, например создать кластер БД, создать или удалить хост в кластере.

Помимо этого роль `[!KEYREF roles-editor]` включает в себя все разрешения роли `[!KEYREF roles-viewer]`.

#### [!KEYREF roles-admin]

Пользователь с ролью `[!KEYREF roles-admin]` может управлять правами доступа к ресурсам, например разрешить другим пользователям создавать кластеры БД или просматривать информацию о них.

Помимо этого роль `[!KEYREF roles-admin]` включает в себя все разрешения роли `[!KEYREF roles-editor]`.