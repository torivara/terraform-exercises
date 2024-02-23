### Exercise 8: Implementing Azure SQL Database

**Objective**: Create an [Azure SQL Database](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/mssql_database) instance.

**Tasks**:
1. Declare variables for the SQL Database configuration (server name, database name, etc.).
2. Define resources for an Azure SQL Server and a SQL Database.
3. Apply your Terraform configuration to create the SQL Database.

- **Hint**: The database requires an SQL server to be defined first.
- **Hint**: Use a small SKU, preferrably S0 or S1.