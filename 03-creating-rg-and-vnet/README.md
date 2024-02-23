# Exercise 3: Creating a Resource Group and a virtual network (local state)

You need to log in for this exercise. Log in with a regular user or with a service principal. Process described below.

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

## User login

When logging in as a regular user, you can use the az login both with terraform and terraform remote backend.

Login with the below command, and you will be prompted in a separate browser window for login credentials, or just accept if you are already authenticated.

```powershell
az login
```

## Service principal login

Service principal login with az login is not supported when using remote backend. This is only possible with a regular user. Therefore you must [authenticate with environment variables](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/guides/service_principal_client_secret#configuring-the-service-principal-in-terraform).

Replace the values below with values from your credentials as created in prerequisites step of this lab.

Windows/PowerShell

```powershell
# PowerShell
$env:ARM_CLIENT_ID = "00000000-0000-0000-0000-000000000000"
$env:ARM_CLIENT_SECRET = "12345678-0000-0000-0000-000000000000"
$env:ARM_TENANT_ID = "10000000-0000-0000-0000-000000000000"
$env:ARM_SUBSCRIPTION_ID = "20000000-0000-0000-0000-000000000000"
```

Linux/Mac/Bash/Zsh

```bash
# sh
export ARM_CLIENT_ID="00000000-0000-0000-0000-000000000000"
export ARM_CLIENT_SECRET="12345678-0000-0000-0000-000000000000"
export ARM_TENANT_ID="10000000-0000-0000-0000-000000000000"
export ARM_SUBSCRIPTION_ID="20000000-0000-0000-0000-000000000000"
```