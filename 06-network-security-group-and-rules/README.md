### Exercise 6: Deploying an Azure Key Vault

**Objective**: Deploy an [Azure Key Vault](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/key_vault) for secret storage. You should always store secrets in a secure vault.

**Tasks**:
1. Create variables for Key Vault configuration.
2. Use RBAC for authorization.
3. Add role assignment for terraform user.
4. Enable retrieval of secrets on VM deployment.

- **Hint**: Avoid purge protection as this can prevent removal of key vault.
- **Hint**: Remember [role assignment](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/role_assignment) for your Terraform user. [Key Vault Reader](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#key-vault-reader) combined with [Key Vault Secrets User](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#key-vault-secrets-user) should be sufficient (least privilege), but you can also use [Key Vault Administrator](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#key-vault-administrator) in this fictional setting.
