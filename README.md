# liquibase-template

A template for managing database changes with [Liquibase](https://docs.liquibase.com/home.html). This repository provides the basic configuration and workflow for integrating Liquibase into your project.

### Prerequisites

-   [Liquibase CLI](https://formulae.brew.sh/formula/liquibase)
-   [DBeaver](https://dbeaver.io/) (Optional)
-   Access to a relational database (e.g., PostgreSQL)

### Setup

To get started, clone the repository and configure Liquibase for your database:

1.  Clone the repository:

    ```bash
    git clone https://github.com/JesusdelCas99/liquibase-template.git
    ```

2.  Update `liquibase.properties` with your database details:
    -   **changeLogFile**: Path to changelog (e.g., `changelog-master.xml`).
    -   **classpath**: Path to JDBC driver (e.g., `postgresql-42.7.5.jar`).
    -   **url**: Database URL (e.g., `jdbc:postgresql://localhost:5432/your_database`).
    -   **driver**: JDBC driver class (e.g., `org.postgresql.Driver`).
    -   **username**: Database username.
    -   **password**: Database password.

### Workflow

Basic Liquibase workflow involves the following commands:

-   Validate changelog:
    ```bash
    liquibase validate
    ```

-   Apply new changesets:
    ```bash
    liquibase update
    ```

-   Check database status:
    ```bash
    liquibase status
    ```

-   Mark changesets as applied (no execution). Use cautiously, mainly for existing databases: 
    ```bash
    liquibase changelog-sync
    ```

-   Tag a database state. Useful for releases or rollbacks:
    ```bash
    liquibase tag 'v0.2'
    ```
    
-   Rollback to a specific date:
    ```bash
    liquibase rollbackToDate "2025-01-31 15:03:40.125"
    ```

-   Rollback to a specific tag:
    ```bash
    liquibase rollback 'v0.2'
    ```

-   Rollback by changeset count:
    ```bash
    liquibase rollbackCount 1
    ```

    Note: Rollbacks can be irreversible and may cause data loss.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
