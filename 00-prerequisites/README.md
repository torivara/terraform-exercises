# Prerequisites for the lab

**Objective**: Handle prerequisites for the exercises

You need an active Azure Subscription, and an Entra ID tenant where you have at least Application Developer role.

**Tasks**:
1. Install Terraform on your machine (required for running Terraform actions).
2. Install Azure CLI on your machine (required for authenticating Terraform to Azure).
3. Install Hashicorp Terraform extension in VSCode.
4. Create a folder for your Terraform project (c:\terraform\dojo-coding) or something similar. Avoid using spaces in the name as this can cause issues.
5. Add a version.tf and provider.tf in your project. The file content is suggested below in coding blocks.
6. Set a Terraform required version higher than or equal to 1.5.5.
7. [Create a service principal with Azure CLI](https://learn.microsoft.com/en-us/cli/azure/azure-cli-sp-tutorial-1?tabs=bash#create-a-service-principal) for use in later exercises.
   - Write down the output. You will need it later. 
   - Grant the service principal "Owner" permissions on your target subscription.
8. Create a storage account for state storage
9. Initialize your Terraform configuration with `terraform init`

- **Hint**: Use the Terraform documentation to find the syntax for declaring providers and [version constraints](https://developer.hashicorp.com/terraform/language/expressions/version-constraints).
- **Hint**: Use the [documentation](https://developer.hashicorp.com/terraform/language/settings#specifying-provider-requirements) to find how this is configured.
- **Hint**: Use winget (or another package manager) to install Terraform and Azure CLI. This simplifies future software updates.


*version.tf*

```hcl
# ------------------------------------------------------------------------------------------
# This file used to configure versions of the providers used to provision workspace
# ------------------------------------------------------------------------------------------
terraform {
  required_version = ">=1.5"
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "~>3.0"
    }
    random = {
      source  = "hashicorp/random"
      version = "~>3.6"
    },
    null = {
      source  = "hashicorp/null"
      version = "~>3.0"
    }
  }
}
```

*provider.tf*

```hcl
# ------------------------------------------------------------------------------------------
# This file used to configure providers for your workspace.
# Azurerm provider should be present for correct configuration.
# ------------------------------------------------------------------------------------------
provider "azurerm" {
  skip_provider_registration = false
  features {}
}
```

*State storage creation*

```bash
RESOURCE_GROUP_NAME=rg-tfstate
STORAGE_ACCOUNT_NAME=satfstate$RANDOM
CONTAINER_NAME=terraformstate

# Create resource group
az group create --name $RESOURCE_GROUP_NAME --location norwayeast

# Create storage account
az storage account create --resource-group $RESOURCE_GROUP_NAME --name $STORAGE_ACCOUNT_NAME --sku Standard_LRS --encryption-services blob

# Create blob container
az storage container create --name $CONTAINER_NAME --account-name $STORAGE_ACCOUNT_NAME
```