### Exercise 4: Moving the state

**Objective**: Move the state from locally on your client to remotely on Azure Storage Account

**Tasks**:
1. Configure your [AzureRM remote backend](https://developer.hashicorp.com/terraform/language/settings/backends/azurerm) with information provided.
2. Try to plan and apply configuration. What happens?
3. Fix the issues.
4. Apply your configuration with the new remote state.

- **Hint**: Look into [terraform init -migrate-state](https://developer.hashicorp.com/terraform/cli/commands/init#backend-initialization).
