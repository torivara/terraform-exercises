# Basic tasks

Here are some generic basic tasks to perform if you want to get to know Terraform syntax and language specific features.

1. **Create an Output Value:**
   - **Task:** Write a Terraform configuration that declares an input variable to accept a user's name. Use this variable to output a greeting message that says, "Hello, [user's name]!" upon applying the configuration. Ensure the output is clearly visible on the screen.

2. **Define a Map with Authors and Their Books:**
   - **Task:** Define a map in Terraform that lists at least three authors as keys and arrays of book titles they've written as values. Create an output that neatly formats this information, so it's readable upon apply, e.g., "Author Name: [Book1, Book2, Book3]."

3. **Create a List and Display Its Contents:**
   - **Task:** Create a Terraform list variable containing names of either superheroes or TV series (choose one theme). Write a configuration that iterates over this list and outputs each name with a prefix, e.g., "Superhero: Superman" or "TV Series: Breaking Bad," upon applying.

4. **Use Conditional Expressions:**
   - **Task:** Write a Terraform configuration that takes an input variable indicating a deployment environment (e.g., "prod" or "dev"). Use a conditional expression to output a message that changes based on the environment, such as "Deploying to Production" for "prod" and "Deploying to Development" for "dev".

5. **Combine Two Lists with a Function:**
   - **Task:** Define two list variables in Terraform, each with different content. Use the `concat` function to combine these lists into a new list. Output the combined list to ensure all elements from both lists are included.

6. **Find the Largest Number in a List:**
   - **Task:** Create a local list variable in Terraform that contains numerical values. Use the `max` function to find the largest number in the list. Output this number with a message, such as "The largest number is: [number]."

7. **Sort a List of Numbers:**
   - **Task:** Following the previous task, write a configuration that sorts the list of numbers in ascending order using the `sort` function. Output the sorted list to verify the order.

8. **Run a Local Script with Terraform:**
   - **Task:** Create a simple script in either PowerShell or Bash that outputs "Hello, Terraform!" to the console. Use a Terraform `null_resource` and the `local-exec` provisioner to run this script when applying your Terraform configuration.

9. **Work with a Local JSON File:**
   - **Task:** Create a local JSON file containing some configuration data (e.g., configurations for an application). Use Terraform to read this file into a local variable and output something simple from it, like a version number or a name.
   - **Follow-up Question:** After making a change to the JSON file (e.g., updating a version number), apply your Terraform configuration again and observe what happens. Discuss how Terraform's state reflects changes in local files between plans.

10. **Working with maps and variables:**
    - **Task:** Define two maps with superheroes from dc and marvel. Map keys should be superhero name and value should be secret identity. Combine the maps with a function in a local variable.
    - **Task:** List all superheroes in output.
    - **Task:** Filter heroes by name length.
    - **Task:** Find the secret identity for a super hero.
    - **Task:** Test other map and string manipulation if time allows.