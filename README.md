# Exercises for Dojo coding session 2024-02-22

These are the exercises we will try to get through during our dojo coding session.

## General guidelines

- Avoid using AI to generate your code. This limits how much of it you understand when finished.
- There are pre-created users for you to authenticate to the lab.
- The lab allows only creation of the resources mentioned in this exercise.
- Please avoid creation of extremes (such as many VMs or databases). The lab is not free.
- Users will be deactivated end of working day 2024-02-24.
- All resources created in the lab environment will be forcefully deleted end of working day 2024-02-24.
- **Absolutely no bitcoin mining or any other shenanigans! Microsoft detects this and blocks the Azure tenant without notice.**
- Use git for version control if you want, this is not covered in our workshop.

You can find solutions [here](https://www.google.com).

### Exercise 1: Setting Up Your Environment (local state)

**Objective**: Install prerequisites and configure it to use the AzureRM provider.

**Tasks**:
1. Install Terraform on your machine (required for running Terraform actions).
2. Install Azure CLI on your machine (required for authenticating Terraform to Azure).
3. Install Hashicorp Terraform extension in VSCode.
4. Configure your Terraform and provider version constraints with a `version.tf` file.
5. Configure Terraform to use the [AzureRM provider](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs) by creating a `provider.tf` file.
7. Initialize your Terraform configuration.

- **Hint**: Use the Terraform documentation to find the syntax for declaring providers and initializing configurations.
- **Hint**: Use winget (or another package manager) to install Terraform and Azure CLI. This simplifies future software updates.

### Exercise 2: Defining Variables, Locals, and Outputs (local state)

**Objective**: Learn to declare variables, locals, and outputs.

**Tasks**:
1. Create a `variables.tf` file to declare variables.
2. Define a variable called prefix in your `variables.tf` file.
3. Define a variable called resource_group_name in your variables.tf file.
4. Define a local variable in `locals.tf` to concatenate the prefix with the resource group name.
5. Create an output in `outputs.tf` to display the full resource group name.
6. Run terraform plan to see changes.
7. Run terraform apply to output values.

- **Hint**: Explore Terraform documentation on variables, locals, and outputs.

### Exercise 3: Creating a Resource Group and a virtual network (local state)

**Objective**: Use Terraform to create an [Azure Resource Group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/resource_group), and create a [Virtual Network](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_network) within the Resource Group.

**Tasks**:
1. Using the variable and local from Exercise 2, define a resource in `main.tf` to create an Azure Resource Group.
2. Add another variable in `variables.tf` called location. You can add a sensible default value if you want.
3. Validate the location variable to allow only locations: "norwayeast", "norwaywest", "westeurope", "northeurope"
4. Add new variables for the Virtual Network settings (address space, location, default subnet).
5. Define a resource in your Terraform configuration to create a Virtual Network in the previously created Resource Group.
6. Plan and apply your configuration to create the resource group in Azure.

- **Hint**: Refer to the AzureRM provider documentation for the syntax to create a resource group.
- **Hint**: Terraform validation for variables documentation [here](https://developer.hashicorp.com/terraform/language/values/variables#custom-validation-rules)
- **Hint**: Look into the AzureRM Virtual Network resource documentation.

### Exercise 4: Moving the state

**Objective**: Move the state from locally on your client to remotely on Azure Storage Account

**Tasks**:
1. Configure your [AzureRM remote backend](https://developer.hashicorp.com/terraform/language/settings/backends/azurerm) with information provided.
2. Try to plan and apply configuration. What happens?
3. Fix the issues.
4. Apply your configuration with the new remote state.

- **Hint**: Look into [terraform init -migrate-state](https://developer.hashicorp.com/terraform/cli/commands/init#backend-initialization).

### Exercise 5: Subnets Creation

**Objective**: Create more [subnets](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/subnet) within your Virtual Network.

**Tasks**:
1. Declare a map variable for subnet configurations.
2. Reference the virtual network with a property lookup and not a hardcoded vnet name.
3. Update your Terraform configuration to include subnets in your Virtual Network.
4. Apply your changes to Azure.
5. Remove a subnet from your config. What happens when you plan and apply?

- **Hint**: Each subnet will be a separate resource linked to your Virtual Network.
- **Hint**: Explore [for_each](https://developer.hashicorp.com/terraform/language/meta-arguments/for_each) to create more subnets without repeating your code.
- **Alternative solution**: Try creating the same subnets inside the virtual network resource with a dynamic block. Is this easier? Harder? Same?

### Exercise 6: Deploying an Azure Key Vault

**Objective**: Deploy an [Azure Key Vault](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/key_vault) for secret storage. You should always store secrets in a secure vault.

**Tasks**:
1. Create variables for Key Vault configuration.
2. Use RBAC for authorization.
3. Add role assignment for terraform user.
4. Enable retrieval of secrets on VM deployment.

- **Hint**: Avoid purge protection as this can prevent removal of key vault.
- **Hint**: Remember [role assignment](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/role_assignment) for your Terraform user. [Key Vault Reader](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#key-vault-reader) combined with [Key Vault Secrets User](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#key-vault-secrets-user) should be sufficient (least privilege), but you can also use [Key Vault Administrator](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#key-vault-administrator) in this fictional setting.

### Exercise 7: Deploying an Azure VM

**Objective**: Deploy an Azure Virtual Machine (with public IP address).

**Tasks**:
1. Create variables for VM configuration (image, size, etc.).
2. Determine connection method (SSH for linux, RDP for windows).
3. Determine authentication method (SSH key pair or password for linux, user/pass for windows).
4. Provide credentials in a secure way (not hardcoded). Use Key Vault from previous task for secrets storage and retrieval if using passwords.
5. Define a resource for an Azure VM, placing it within your subnet. Public IP required for external access.
6. Apply your Terraform configuration to deploy the VM.

- **Hint**: Avoid the deprecated azurerm_virtual_machine resource. Use [linux](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/linux_virtual_machine) or [windows](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/windows_virtual_machine).

### Exercise 8: Implementing Azure SQL Database

**Objective**: Create an [Azure SQL Database](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/mssql_database) instance.

**Tasks**:
1. Declare variables for the SQL Database configuration (server name, database name, etc.).
2. Define resources for an Azure SQL Server and a SQL Database.
3. Apply your Terraform configuration to create the SQL Database.

- **Hint**: The database requires an SQL server to be defined first.
- **Hint**: Use a small SKU, preferrably S0 or S1.

### Exercise 9: Network Security Group and Rules

**Objective**: Implement a [Network Security Group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_security_group) (NSG) with security rules.

**Tasks**:
1. Define a NSG resource with security rules in Terraform.
2. The NSG should allow HTTPS, SSH and RDP from your client ip to the entire subnet range.
3. Define the [NSG rules](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_security_rule) with a map of objects.
4. Associate the NSG with one or more subnets from Exercise 5.
5. Apply your configuration.

- **Hint**: Security rules should not be defined within the NSG resource block. Use the NSG rule resource with for_each.
- **Hint**: Use [dynamic blocks](https://developer.hashicorp.com/terraform/language/expressions/dynamic-blocks) for your NSG rules.
- **Hint**: Get your public ip `curl api.ipify.org` or `(invoke-webrequest api.ipify.org).content`

### Exercise 10: Create a module

**Objective**: Create a module out of one of the previous resources you made.

**Tasks**:
1. Create a new folder for the module and copy the terraform files you need from previous exercises.
2. Declare variables for the module. Make it as flexible as possible.
3. Define a resource with your module.
4. Apply your Terraform configuration to create the resource(s).

- **Hint**: Think about flexibility and reuse when creating modules.
- **Hint**: Define smart defaults to allow minimal variable input when using module.
- **Hint**: [Conditional expressions](https://developer.hashicorp.com/terraform/language/expressions/conditionals) allows you to handle input missing from module calls.

### Exercise 11: Adding Application Gateway

**Objective**: Set up an [Application Gateway](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/application_gateway) to route traffic to your VM.

**Tasks**:
1. Define variables for the Application Gateway configuration.
2. Create an Application Gateway resource in Terraform, configuring backend pools, listeners, and rules.
3. Apply your configuration to establish the Application Gateway.

- **Hint**: Use the AzureRM documentation for Application Gateway to understand the required components and dependencies.
