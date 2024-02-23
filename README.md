# Exercises for Dojo coding session 2024-02-22

These are the exercises we will try to get through during our dojo coding session.

## General guidelines

- Look up the resource type needed in [AzureRM Provider Docs](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs) and work from there.
- If you have Hashicorp Terraform extension in VSCode you can enable [code completion](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform#code-completion).
- There are pre-created users for you to authenticate to the lab.
- The lab allows only creation of the resources mentioned in this exercise.
- Please avoid creation of extremes (such as many VMs or databases). The lab is not free.
- Users will be deactivated end of working day 2024-02-24.
- All resources created in the lab environment will be forcefully deleted end of working day 2024-02-24.
- **Absolutely no bitcoin mining or any other shenanigans! Microsoft detects this and blocks the Azure tenant without notice.**
- Use git for version control if you want, this is not covered in our workshop.
- In all tasks you can, and should, use some form of formatting tool. This can either be [autoformat](https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform#formatting) or manually with `terraform fmt`.
- In all tasks you should try `terraform validate` before plan and apply to see that you have the syntax correct.

You can find solutions [here](https://github.com/torivara/dojo-terraform-solutions) some time during the workshop (not immediately).

- [Prerequisites](/00-prerequisites/)
  - **Objective**: Install software and create needed resources
- [Exercise 1: Optional exercises](/01-optional-syntax-exercises/)
  - **Objective**: Getting to know functions, expressions, variable types.
- [Exercise 2: Defining Variables, Locals, and Outputs](/02-variables-locals-outputs/)
  - **Objective**: Learn to declare variables, locals, and outputs.
- [Exercise 3: Creating a Resource Group and a virtual network](/03-creating-rg-and-vnet/)
  - **Objective**: Use Terraform to create an [Azure Resource Group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/resource_group), and create a [Virtual Network](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_network) within the Resource Group.
- [Exercise 4: Moving the state](/04-move-state/)
  - **Objective**: Move the state from locally on your client to remotely on Azure Storage Account
- [Exercise 5: Subnets Creation](/05-subnets-creation/)
  - **Objective**: Create more [subnets](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/subnet) within your Virtual Network.
- [Exercise 6: Deploying an Azure Key Vault](/06-deploying-azure-keyvault/)
  - **Objective**: Deploy an [Azure Key Vault](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/key_vault) for secret storage. You should always store secrets in a secure vault.
- [Exercise 7: Deploying an Azure VM](/07-deploying-azure-vm/)
  - **Objective**: Deploy an Azure Virtual Machine (with public IP address).
- [Exercise 8: Implementing Azure SQL Database](/08-implement-azure-sql-database/)
  - **Objective**: Create an [Azure SQL Database](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/mssql_database) instance.
- [Exercise 9: Network Security Group and Rules](/09-create-nsg-with-rules/)
  - **Objective**: Implement a [Network Security Group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_security_group) (NSG) with security rules.
- [Exercise 10: Create a module](/10-create-a-module/)
  - **Objective**: Create a module out of one of the previous resources you made.
- [Exercise 11: Adding Application Gateway](/11-add-application-gateway/)
  - **Objective**: Set up an [Application Gateway](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/application_gateway) to route traffic to your VM.
- [Exercise 12: Advanced optional exercises](/12-advanced-optional-exercises/)
  - **Objective**: More advanced exercises for those that are done with the previous deployment tasks.
