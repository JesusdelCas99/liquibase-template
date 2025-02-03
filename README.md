# liquibase-template

A template for managing database changes with Liquibase. This repository provides the basic configuration and workflow for integrating Liquibase into your project.

### Prerequisites

-   [Liquibase](https://formulae.brew.sh/formula/liquibase) for managing database changes.
-   [DBeaver](https://dbeaver.io/) for database visualization and management (optional).
-   Access to a relational database (e.g., PostgreSQL).

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

#### Core Commands:

-   **Validate changelog**: Verify the syntax and structure of your changelog file:
    ```bash
    liquibase validate
    ```

-   **Apply new changesets**: Deploy pending changesets to the target database:
    ```bash
    liquibase update
    ```

-   **Check database status**: Review the deployment status of changesets:
    ```bash
    liquibase status
    ```

-   **Synchronize changelog**: Mark changesets as applied without executing them. 
    ```bash
    liquibase changelog-sync
    ```

-   **Tag database state**: Create a snapshot of the database schema (useful for releases or rollbacks):
    ```bash
    liquibase tag 'v0.2'
    ```

#### Rollback Operations:

Rollback operations can be irreversible and may result in data loss. Exercise caution and ensure proper backups are in place before executing rollback commands.

-   **Rollback to date**: Revert the database to a specific point in time:
    ```bash
    liquibase rollbackToDate "2025-01-31 15:03:40.125"
    ```

-   **Rollback to tag**: Revert the database to a previously tagged state:
    ```bash
    liquibase rollback 'v0.2'
    ```

-   **Rollback by count**: Revert a specified number of changesets:
    ```bash
    liquibase rollbackCount 1
    ```

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
