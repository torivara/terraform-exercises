## Advanced Terraform

### 1. Investigate Azure Verified Modules from Microsoft

**Objective:** Understand and find Azure Verified Modules that can be used with Terraform to manage Azure resources efficiently.

**Tasks:**
- Visit the AVM website and search for Azure Verified Modules provided by Microsoft.
- Review documentation for each module to understand its capabilities, inputs, and outputs.
- Select modules that are relevant for creating a small Azure environment, focusing on Virtual Networks, Virtual Machines, Load Balancers, and Network Security Groups.

### 2. Look at the Terraform CAF Module from Microsoft

**Objective:** Explore the Terraform Cloud Adoption Framework (CAF) module for Azure, designed to help organizations adopt Azure following best practices.

**Tasks:**
- Find the Terraform CAF module on the Terraform Registry or GitHub, provided by Microsoft. Avoid the aztfcaf module which is unneccessary complex.
- Review the module's documentation to understand how it structures Azure environments, including considerations for networking, security, and compute resources.
- Identify how the CAF module can be leveraged to create your small environment, paying attention to modular architecture and environment segregation (dev/test/prod).

### 3. Create a Small Environment

**Objective:** Use Terraform modules to define and deploy a small Azure environment consisting of essential networking and compute resources.

**Tasks:**
- **Azure Virtual Network:** Use a module to create a virtual network with a subnet.
- **Azure Virtual Machine:** Deploy a virtual machine within the subnet of your virtual network. Consider using a module that allows specifying VM size, image, and networking settings.
- **Azure Load Balancer:** Set up a load balancer to distribute traffic to your virtual machine(s). Use a module that supports basic load balancer configuration.
- **Azure Network Security Group:** Implement network security group rules to control access to the virtual machine(s).

### 4. Establish a Policy Assignment for Deny

**Objective:** Implement a policy to deny specific actions or enforce configurations at the resource group level.

**Tasks:**
- Use the `azurerm_policy_definition` and `azurerm_policy_assignment` resources to define and assign a policy.
- Example policy could deny the creation of resources not compliant with your organization's standards.

### 5. Manage Multiple Environments

**Objective:** Create dev, test, prod, and staging environments with identical resources but differentiated by naming conventions, tags, or other "soft" values.

**Tasks:**
- Utilize Terraform workspaces or a modular approach with variable inputs to manage multiple environments within the same codebase.
- Define a naming convention that includes the environment type in resource names and tags to distinguish between environments.
- Ensure that configurations for each environment are identical except for names, tags, and possibly other environment-specific parameters like size or capacity.

```hcl
variable "environment" {
  description = "Deployment environment (dev/test/prod/staging)"
}

# Use the variable in resource names, tags, etc.
resource "azurerm_resource_group" "example" {
  name     = "rg-${var.environment}-example"
  location = "East US"
  tags = {
    Environment = var.environment
  }
}

# Similar approach for other resources, with adjustments for each environment as necessary
```

### 6. Checkout the CAF naming module

**Objective:** Investigate the [azurecaf naming module](https://github.com/aztfmod/terraform-provider-azurecaf).

**Tasks:**
- Use the naming module to create some resource names.
- Output the resource names without actually creating the resources.
- How are the names generated? How many different resource types can you generate names for?

```hcl
data "azurecaf_name" "rg_example" {
  name          = "demogroup"
  resource_type = "azurerm_resource_group"
  prefixes      = ["a", "b"]
  suffixes      = ["y", "z"]
  random_length = 5
  clean_input   = true
}

output "rg_example" {
  value = data.azurecaf_name.rg_example.result
}
```