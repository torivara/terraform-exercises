# Exercises for Introduction to Terraform

These are the exercises we will try to get through during our dojo coding session.

## General guidelines

- Look up the resource type needed in [AzureRM Provider Docs](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs) and work from there.
- If you have Hashicorp Terraform extension in VSCode you can enable [code completion](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform#code-completion).
- Use git for version control if you want, this is not covered in our workshop.
- In all tasks you can, and should, use some form of formatting tool. This can either be [autoformat](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform#formatting) or manually with `terraform fmt`.

Solutions will be provided halfway through the workshop.

## Exercises

- [Prerequisites](/00-prerequisites/)
  - **Objective**: Install software and create needed resources
- [Exercise 1: Optional exercises](/01-optional-syntax-exercises/)
  - **Objective**: Getting to know functions, expressions, variable types.
- [Exercise 2: Defining Variables, Locals, and Outputs](/02-variables-locals-outputs/)
  - **Objective**: Learn to declare variables, locals, and outputs.
- [Exercise 3: Creating a Resource Group and a virtual network](/03-creating-rg-and-vnet/)
  - **Objective**: Use Terraform to create an Azure Resource Group, and create a Virtual Network within the Resource Group.
- [Exercise 4: Moving the state](/04-move-state/)
  - **Objective**: Move the state from locally on your client to remotely on Azure Storage Account
- [Exercise 5: Subnets Creation](/05-subnets-creation/)
  - **Objective**: Create more subnets within your Virtual Network.
- [Exercise 6: Deploying an Azure Key Vault](/06-deploying-azure-keyvault/)
  - **Objective**: Deploy an Azure Key Vault for secret storage. You should always store secrets in a secure vault.
- [Exercise 7: Deploying an Azure VM](/07-deploying-azure-vm/)
  - **Objective**: Deploy an Azure Virtual Machine (with public IP address).
- [Exercise 8: Implementing Azure SQL Database](/08-implement-azure-sql-database/)
  - **Objective**: Create an Azure SQL Database instance.
- [Exercise 9: Network Security Group and Rules](/09-create-nsg-with-rules/)
  - **Objective**: Implement a Network Security Group (NSG) with security rules.
- [Exercise 10: Create a module](/10-create-a-module/)
  - **Objective**: Create a module out of one of the previous resources you made.
- [Exercise 11: Adding Application Gateway](/11-add-application-gateway/)
  - **Objective**: Set up an Application Gateway to route traffic to your VM.
- [Exercise 12: Advanced optional exercises](/12-advanced-optional-exercises/)
  - **Objective**: More advanced exercises for those that are done with the previous deployment tasks.
