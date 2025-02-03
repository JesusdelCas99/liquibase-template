# liquibase-template

A template for managing database changes with [Liquibase](https://docs.liquibase.com/home.html). This repository provides the basic configuration and workflow for integrating Liquibase into your project.

### Prerequisites

- [Liquibase](https://formulae.brew.sh/formula/liquibase) for managing database changes
- [DBeaver](https://dbeaver.io/) for database visualization and management
- Access to a relational database (e.g., PostgreSQL)

### Setup

To get started, clone the repository and configure Liquibase for your database:

1. Clone the repository:

    ```bash 
    git clone https://github.com/JesusdelCas99/liquibase-template.git
    ```

2. Update `liquibase.properties` with your database details:
    - **changeLogFile**: Path to the changelog file (e.g., `changelog-master.xml`).
    - **classpath**: Path to the JDBC driver (e.g., `postgresql-42.7.5.jar`).
    - **url**: Database connection URL (e.g., `jdbc:postgresql://localhost:5432/your_database`).
    - **driver**: JDBC driver class (e.g., `org.postgresql.Driver`).
    - **username**: Database username.
    - **password**: Database password.

### Usage

The basic Liquibase workflow includes the following actions to manage and apply changes to your database schema:

- Validate the Liquibase changelog for errors:
    
    ```bash
    liquibase validate
    ```

- Apply unregistered changesets from the changelog to the target database and register them in the `databasechangelog` table (created if absent):

    ```bash
    liquibase update
    ```

- Report database schema synchronization:
    
    ```bash
    liquibase status
    ```

- Register changesets as applied (no execution):

    ```bash
    liquibase changelog-sync
    ```

- Rollback to a specific date:

    ```bash
    liquibase rollbackToDate "2025-01-31 15:03:40.125"
    ```

- Rollback to a specific tag:
    
    ```bash
    liquibase rollback 'v0.1'
    ```

- Rollback by count of changesets:

    ```bash
    liquibase rollbackCount 1
    ```

    Note: Rollback action is not reversible and may result in data loss.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
