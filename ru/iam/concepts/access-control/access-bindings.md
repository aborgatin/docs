# Привязка прав доступа

_Привязка прав доступа_ — это назначение роли пользователю по отношению к указанному ресурсу.

Сначала вы выбираете ресурс, а потом задаете права доступа для этого ресурса. Права доступа задаются в виде списка связей _роль-пользователь_. Вы можете добавлять и удалять эти связи, таким образом контролируя права доступа к ресурсу.

Например, если вы хотите выдать пользователю _ivan@yandex.ru_ роли `[!KEYREF roles-cloud-member]` и `[!KEYREF roles-viewer]` для просмотра ресурсов в вашем облаке, вам потребуется создать две связи _роль-пользователь_, для каждой из ролей. При запросе через API тело этого запроса будет выглядеть так:

```
{
  "resourceId": "<cloud-id>",
  "accessBindings": [
    {
      "roleId": "[!KEYREF roles-cloud-member]",
      "subject": { "id": "<user-id>", "type": "userAccount" }
    }, {
      "roleId": "[!KEYREF roles-viewer]",
      "subject": { "id": "<user-id>", "type": "userAccount" }
    }, {
  ]
}
```

где:
- `<cloud-id>` — идентификатор облака, на которое выдаются права доступа;
- `<user-id>` — идентификатор пользователя, которому выдаются права доступа.

Не ко всем ресурсам можно привязывать права доступа. На данный момент управлять правами доступа можно только для следующих ресурсов: облако, каталог, сервисный аккаунт.

Права доступа на ресурс могут наследоваться от других ресурсов. Например, новый диск создается в каталоге, а каталог в облаке. Права доступа на диск наследуются от прав на каталог и облако, в которых находится этот диск. Подробнее о наследовании прав и ресурсной модели Яндекс.Облака читайте в разделе [[!TITLE]](../../../resource-manager/concepts/resources-hierarchy.md) документации сервиса [!KEYREF resmgr-full-name].

#### См. также
- [[!TITLE]](../access-control/roles.md)

