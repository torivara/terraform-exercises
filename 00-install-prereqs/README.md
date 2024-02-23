### Exercise 0: Setting Up Your Environment (local state)

**Objective**: Install prerequisites and configure it to use the AzureRM provider.

**Tasks**:
1. Install Terraform on your machine (required for running Terraform actions).
2. Install Azure CLI on your machine (required for authenticating Terraform to Azure).
3. Install Hashicorp Terraform extension in VSCode.
4. Create a folder for your Terraform project (c:\terraform\dojo-coding) or something similar. Avoid using spaces in the name as this can cause issues.
5. Configure your Terraform and provider terraform and provider versions with a `version.tf` file.
6. Configure Terraform to use the [AzureRM provider](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs) by creating a `provider.tf` file.
7. Initialize your Terraform configuration.
8. Run terraform plan and apply to see if there are changes needed and the config is valid.

- **Hint**: Use the Terraform documentation to find the syntax for declaring providers and [version constraints](https://developer.hashicorp.com/terraform/language/expressions/version-constraints).
- **Hint**: Use the [documentation](https://developer.hashicorp.com/terraform/language/settings#specifying-provider-requirements) to find how this is configured.
- **Hint**: Use winget (or another package manager) to install Terraform and Azure CLI. This simplifies future software updates.