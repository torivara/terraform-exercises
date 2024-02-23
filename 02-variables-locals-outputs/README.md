# Exercise 2: Defining Variables, Locals, and Outputs (local state)

**Objective**: Learn to declare variables, locals, and outputs. Use this exercise to make some variables and get to know them.

**Tasks**:
1. Create a `variables.tf` file to declare variables.
2. Define a variable called prefix in your `variables.tf` file.
3. Define a variable called resource_group_name in your `variables.tf` file.
4. Define a local variable in `locals.tf` to concatenate the prefix with the resource group name.
5. Create an output in `outputs.tf` to display the full resource group name.
6. Run terraform plan to see changes.
7. Run terraform apply to output values.

- **Hint**: Explore Terraform documentation on variables, locals, and outputs.

## Tips

Terraform does not care what your file names are as long as they end with .tf. On terraform plan or apply, all .tf-files in the current directory will be merged and processed. The naming and splitting into different files is purely for human readability.

That said, this is the recommended terraform files in a basic project folder:

- terraform-project
  - **modules** (a folder for any local modules you would need)
  - **env** (a folder for declaring different setup for different environments. These can then call the main module, if need be.)
  - *provider.tf* (declares required providers)
  - *version.tf* (declares specific provider configuration if applicable)
  - *variables.tf* (declares all your terraform variables)
  - *locals.tf* (highly optional, but you can gather all your local blocks here if you want)
  - *outputs.tf* (declares all outputs from your terraform project)
  - *main.tf* (often declares common resources for this state like shared resource groups or subscription config)

Locals block is mostly used for repeated or calculated values inside the terraform project and is defined like this:

```hcl
locals {
  local_variable = "this is a locals variable"
}

# This is how you reference a local variable
output "local" {
  value = local.local_variable
}
```

Variables are used to input values into the terraform project, and is mostly applicable for modules, but also for regular projects.

```hcl
variable "teststring" {
  type = string
  description = "This is a string variable"
  default = "defaultValue"
}

variable "testnumber" {
  type = number
  description = "This is a number variable"
  default = 1
}

# Variables are referenced like this

output "string_output" {
  value = var.teststring
}

output "number_output" {
  value = var.testnumber
}
```

Variables can be entered in different ways:

- When running terraform plan you will be prompted for variables with no default value (if not provided elsewhere)
- tfvars file that you reference when running terraform plan
- auto tfvars file that terraform automatically fetches variables from
- environment variables that are prefixed with "TF_VAR_variablename"