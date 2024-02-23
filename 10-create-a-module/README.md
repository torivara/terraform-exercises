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