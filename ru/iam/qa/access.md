# Вход в систему и доступ к ресурсам

#### Как войти в консоль управления?

Перейдите на [страницу консоли управления](https://console.cloud.yandex.ru/).

Если вы еще не вошли в ваш аккаунт на Яндексе или Яндекс.Коннекте, нажмите **Войти**. Если у вас еще нет аккаунта, нажмите **Зарегистрироваться**. Подробнее читайте в [документации Яндекс.Паспорта](https://yandex.ru/support/passport/auth.html).

#### Как проверяются права доступа?

Перед тем, как выполнить операцию с ресурсом, например создать виртуальную машину, [!KEYREF iam-short-name] проверяет, есть ли все необходимые разрешения у пользователя. Если какого-то из разрешений нет, операция не будет выполнена и Яндекс.Облако сообщит об ошибке. Подробнее читайте в разделе [[!TITLE]](../concepts/access-control/index.md).

#### Что такое ресурс?

_Ресурс_ — это сущность Яндекс.Облака, с которой вы можете выполнять операции: создавать, изменять, просматривать или удалять. Примеры ресурсов: виртуальные машины, диски, сервисные аккаунты, облака и каталоги. Подробнее читайте в разделе [[!TITLE]](../../resource-manager/concepts/resources-hierarchy.md) документации сервиса [!KEYREF resmgr-name].

#### Что такое привязка прав доступа?

Права доступа к ресурсу задаются в виде списка связей _роль-субъект_. Такие связи называются — привязки прав доступа (access bindings). Вы можете добавлять и удалять эти связи, таким образом контролируя права доступа к ресурсу. Подробнее читайте в разделе [[!TITLE]](../concepts/access-control/index.md#access-bindings).