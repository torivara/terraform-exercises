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
