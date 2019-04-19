# Revoke a role for a resource

If you want to prohibit a [subject](../../concepts/access-control/index.md#subject) from accessing a resource, revoke the subject's roles for that resource or the resource that the access rights are inherited from. For more information, see the section [[!TITLE]](../../concepts/access-control/index.md).

> [!NOTE]
>
> If you need to temporarily revoke all access rights from a user with a Yandex account, you can just revoke the role of `[!KEYREF roles-cloud-member]`. Although the user keeps all the other roles, they can't perform any operations with the cloud resources. When you add the user to the cloud again, the access rights will already be configured.

## How to revoke a role {#revoke-one-role}

---

**[!TAB Management console]**

In the management console, you can only revoke a cloud or folder role:

1. Open the [Access management](https://console.cloud.yandex.ru/iam) page for the selected cloud. If necessary, [switch to another cloud](../../../resource-manager/operations/cloud/switch-cloud.md).
1. In the line with the appropriate user name, click **Configure roles**.
1. Click the x next to the role to remove it. In the **Roles for the cloud** section, you can delete the roles assigned to this user in this cloud. In the **Roles in folders** section, you can delete roles assigned to a user for a folder.

**[!TAB CLI]**

To revoke a role from a subject, delete the corresponding access binding for the appropriate resource:

1. See which users are assigned roles to the resource and what the roles are:
    `yc <SERVICE-NAME> <RESOURCE> list-access-bindings <RESOURCE-NAME>|<RESOURCE-ID>`

    For example, see the `default` folder access bindings:

    ```
    $  yc resource-manager folder list-access-bindings default
    +---------------------+----------------+----------------------+
    |       ROLE ID       |  SUBJECT TYPE  |      SUBJECT ID      |
    +---------------------+----------------+----------------------+
    | editor              | serviceAccount | ajepg0mjas06siuj5usm |
    | viewer              | userAccount    | aje6o61dvog2h6g9a33s |
    +---------------------+----------------+----------------------+
    ```

1. To delete an access binding, run:

    ```
    yc <SERVICE-NAME> <RESOURCE> remove-access-binding <RESOURCE-NAME>|<RESOURCE-ID> \
        --role <ROLE-ID> \
        --subject <SUBJECT-TYPE>:<SUBJECT-ID>
    ```

    where:
    * `<SERVICE-NAME>` is the name of the service  that the resource belongs to (for example, `resource-manager`).
    * `<RESOURCE>` is the category of the resource, such as `folder`.
    * `<RESOURCE-NAME>` is the resource name. You can specify a resource by its name or identifier.
    * `<RESOURCE-ID>` is the resource identifier.
    * `<ROLE-ID>`  is the identifier of the role to revoke (such as `[!KEYREF roles-cloud-owner]`).
    * `<SUBJECT-TYPE>`  is the type of the [subject](../../concepts/access-control/index.md#subject) to revoke the role from.
    * `<SUBJECT-ID>` is the identifier of the subject.

    For example, to revoke a role from the user with the `aje6o61dvog2h6g9a33s` ID:

    ```
    $ yc resource-manager folder remove-access-binding default \
        --role viewer \
        --subject userAccount:aje6o61dvog2h6g9a33s
    ```

**[!TAB API]**

To revoke a resource role from a subject, delete the corresponding access binding. For example, revoke from the user the role for the `b1gvmob95yysaplct532` folder:

1. You can find out who resource roles are assigned to and what the roles are by using the `listAccessBindings` method:

    ```
    $ export FOLDER_ID=b1gvmob95yysaplct532
    $ export IAM_TOKEN=CggaATEVAgA...
    $ curl -H "Authorization: Bearer ${IAM_TOKEN}" "https://resource-manager.api.cloud.yandex.net/resource-manager/v1/folders/${FOLDER_ID}:listAccessBindings"

    {
     "accessBindings": [
      {
       "subject": {
        "id": "ajei8n54hmfhuk5nog0g",
        "type": "userAccount"
       },
       "roleId": "editor"
      }
     ]
    }
    ```

1. Create a request body, for example, in a `body.json` file. In the request body, specify which access binding to delete.

    **body.json:**

    ```json
    {
        "accessBindingDeltas": [{
            "action": "REMOVE",
            "accessBinding": {
                "roleId": "editor",
                "subject": {
                    "id": "ajei8n54hmfhuk5nog0g",
                    "type": "userAccount"
                    }
                }
            }
        ]
    }
    ```

1. Revoke the role by deleting the specified access binding:

    [!INCLUDE [grant-role-folder-via-curl](../../../_includes/iam/grant-role-folder-via-curl.md)]

---
