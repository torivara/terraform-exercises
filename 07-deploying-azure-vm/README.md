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