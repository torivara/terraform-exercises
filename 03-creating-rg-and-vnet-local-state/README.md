### Exercise 3: Creating a Resource Group and a virtual network (local state)

You need to log in for this exercise. Use the provided service principal credentials with the following cli command:

- *Replace myServicePrincipalId with appId*
- *Replace myServicePrincipalPassword with password*

```powershell
az login --service-principal \
         --username myServicePrincipalId \
         --password myServicePrincipalPassword \
         --tenant myOrganizationTenantID
```

You also have access to a portal user if you want to view changes there. This user only has reader access on the subscription and in Entra ID. Log in [here](https://portal.azure.com) with credentials provided. Remember to use private or incognito browser window.

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
