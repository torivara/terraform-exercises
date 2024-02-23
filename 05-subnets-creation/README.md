### Exercise 5: Subnets Creation

**Objective**: Create more [subnets](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/subnet) within your Virtual Network.

**Tasks**:
1. Declare a map variable for subnet configurations.
2. Reference the virtual network with a property lookup and not a hardcoded vnet name.
3. Update your Terraform configuration to include subnets in your Virtual Network.
4. Apply your changes to Azure.
5. Remove a subnet from your config. What happens when you plan and apply?

- **Hint**: Create these subnets either [inline in the virtual network](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/virtual_network#subnet) or use the dedicated [azurerm_subnet](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/subnet) resource. Either way works fine, but they are mutually exclusive!
- **Hint**: Explore [for_each](https://developer.hashicorp.com/terraform/language/meta-arguments/for_each) to create more subnets without repeating your code.
- **Hint**: Dynamic blocks are crucial to adhere to the Don'tRepeatYourself (DRY) principle.
- **Alternative solution**: Try creating the same subnets inside the virtual network resource with a dynamic block. Is this easier? Harder? Same?

*variables.tf*

Suggested map structure

```hcl
variable "subnets" {
  type = map(object({
    address_prefixes = list(string),
    name = string, 
    resource_group_name = string, 
    virtual_network_name = string 
  }))
  default = {
    default = {
      address_prefixes     = ["10.0.0.0/24"]
      name                 = "default"
      resource_group_name  = "rgname"
      virtual_network_name = "vnetname"
    },
    ApplicationGatewaySubnet = {
      address_prefixes     = ["10.0.1.0/24"]
      name                 = "ApplicationGatewaySubnet"
      resource_group_name  = "rgname"
      virtual_network_name = "vnetname"
    }
  }
}
```

*main.tf*

Example of a dynamic block

```hcl
locals {
    inbound_ports = [80, 443]
    outbound_ports = [443, 1433]
}

# Security Groups
resource "aws_security_group" "sg-webserver" {
    vpc_id              = aws_vpc.vpc.id
    name                = "webserver"
    description         = "Security Group for Web Servers"

    dynamic "ingress" {
        for_each = local.inbound_ports
        content {
            from_port   = ingress.value
            to_port     = ingress.value
            protocol    = "tcp"
            cidr_blocks = [ "0.0.0.0/0" ]
        }
    }

    dynamic "egress" {
        for_each = local.outbound_ports
        content {
            from_port   = egress.value
            to_port     = egress.value
            protocol    = "tcp"
            cidr_blocks = [ var.vpc-cidr ]
        }
    }
}
```