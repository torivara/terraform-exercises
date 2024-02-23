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

### Exercise 0: Setting Up Your Environment (local state)

**Objective**: Install prerequisites and configure it to use the AzureRM provider.

### Exercise 1: Basic generic tasks

Do these exercises if you are not familiar with Terraform to get a feel for the syntax.

**Objective**: Getting to know functions, expressions, variable types.

There are ten tasks defined [here](https://github.com/torivara/dojo-terraform/blob/main/01-basic-generic-tasks/exercises.md). Do them at your own pace, and if you feel like getting to know the HCL syntax before starting some resource creation in Azure.

### Exercise 2: Defining Variables, Locals, and Outputs (local state)

**Objective**: Learn to declare variables, locals, and outputs.

### Exercise 3: Creating a Resource Group and a virtual network (local state)

**Objective**: Use Terraform to create an [Azure Resource Group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/resource_group), and create a [Virtual Network](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_network) within the Resource Group.

### Exercise 4: Moving the state

**Objective**: Move the state from locally on your client to remotely on Azure Storage Account

### Exercise 5: Subnets Creation

**Objective**: Create more [subnets](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/subnet) within your Virtual Network.

### Exercise 6: Deploying an Azure Key Vault

**Objective**: Deploy an [Azure Key Vault](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/key_vault) for secret storage. You should always store secrets in a secure vault.

### Exercise 7: Deploying an Azure VM

**Objective**: Deploy an Azure Virtual Machine (with public IP address).

### Exercise 8: Implementing Azure SQL Database

**Objective**: Create an [Azure SQL Database](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/mssql_database) instance.

### Exercise 9: Network Security Group and Rules

**Objective**: Implement a [Network Security Group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_security_group) (NSG) with security rules.

### Exercise 10: Create a module

**Objective**: Create a module out of one of the previous resources you made.

### Exercise 11: Adding Application Gateway

**Objective**: Set up an [Application Gateway](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/application_gateway) to route traffic to your VM.
