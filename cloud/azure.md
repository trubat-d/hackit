# Azure

Azure CLI Syntax

```
az GROUP SUBGROUP ACTION OPTIONAL_PARAMETERS
```

For help

```bash
az -h

#or
az GROUP -h
```

{% tabs %}
{% tab title="Enumeration" %}
Auth user details

```bash
az ad signed-in-user show
```

Enumerate users

```
az ad user list
```

Filter users

```
az ad user list --filter "startsWith('<CHANGETHIS>', displayName)"
```

List Groups

```
az ad group list
```

List members of one group

```
az ad group member list --group "<GROUPNAME>"
```

List group capabilities

```
az role assignment list --assignee <GROUP_ID> --all
```

List keyvaults

```
az keyvault list
```

List if secrets are inside of vault (if user of Key Vault Reader)

```
az keyvault secret list --vault-name <VAULT>
```

List content of the vault (if Key vault Secrets User)

```
az keyvault secret show --vault-name <VAULT_NAME> --name <SECRET_VAULT>
```


{% endtab %}

{% tab title="Session" %}
Clear session (Logout)

```
az account clear
```

Login

```
az login -u EMAIL -p PASSWORD
```


{% endtab %}
{% endtabs %}
