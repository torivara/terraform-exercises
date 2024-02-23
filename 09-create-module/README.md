### Exercise 9: Network Security Group and Rules

**Objective**: Implement a [Network Security Group](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/network_security_group) (NSG) with security rules.

**Tasks**:
1. Define a NSG resource with security rules in Terraform.
2. The NSG should allow HTTPS, SSH and RDP from your client ip to the entire subnet range.
3. Define the NSG rules with a map of objects.
4. Associate the NSG with one or more subnets from Exercise 5.
5. Apply your configuration.

- **Hint**: Use [dynamic blocks](https://developer.hashicorp.com/terraform/language/expressions/dynamic-blocks) for your NSG rules.
- **Hint**: Get your public ip `curl api.ipify.org` or `(invoke-webrequest api.ipify.org).content`