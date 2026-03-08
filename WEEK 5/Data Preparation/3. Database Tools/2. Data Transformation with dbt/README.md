# Data Transformation with dbt (https://www.youtube.com/watch?v=5rNquRnNb4E)

dbt (Data Build Tool) is an open-source tool used for transforming data in modern data pipelines.  
It enables data analysts and engineers to write **SQL-based transformations** while applying **software engineering best practices** such as version control, testing, and documentation.

dbt is typically used in **ELT workflows**, where raw data is first loaded into a data warehouse and then transformed using SQL models.

---

## Key Concepts

### 1. dbt Fundamentals
dbt focuses on the **transformation layer** of the data pipeline.  
Instead of writing complex scripts, transformations are written as **SQL models** that dbt compiles and executes.

Benefits include:
- Modular SQL transformations
- Version control with Git
- Automated testing and documentation
- Dependency management between models

---

## Project Setup

A dbt project can be created using the CLI.

```bash
pip install dbt
dbt init demo_dbt
````

This generates a project structure containing folders such as:

```
models/
analysis/
macros/
tests/
snapshots/
dbt_project.yml
```

The **models folder** is where SQL transformations are written.

---

## dbt Models

A dbt model is simply a **SQL select statement** that transforms data.

Example model:

```sql
with source as (
    select * from {{ source('raw', 'customers') }}
),

renamed as (
    select
        id as customer_id,
        first_name,
        last_name,
        email,
        created_at
    from source
)

select * from renamed
```

dbt compiles this SQL and creates tables or views in the data warehouse.

---

## Materializations

dbt models can be materialized in different ways:

| Type        | Description              |
| ----------- | ------------------------ |
| View        | Creates a database view  |
| Table       | Creates a physical table |
| Incremental | Processes only new data  |

Example configuration:

```sql
{{ config(materialized='table') }}
```

---

## Testing and Documentation

dbt allows built-in **data quality testing**.

Example test:

```yaml
tests:
  - not_null
  - unique
```

It also generates **automatic documentation** for models and datasets.

---

## Jinja Templating

dbt uses **Jinja templating** to make SQL dynamic and reusable.

Example:

```sql
select * from {{ ref('orders') }}
```

This automatically manages dependencies between models.

---

## Sources and Seeds

* **Sources** represent raw data tables.
* **Seeds** allow loading static CSV files into the warehouse.

Example:

```yaml
sources:
  - name: raw
    tables:
      - name: customers
```

---

## Macros and Packages

Macros allow reusable SQL logic.

Example macro:

```sql
{% macro calculate_discount(price) %}
    price * 0.9
{% endmacro %}
```

Packages from the dbt community can also be installed to extend functionality.

---

## Incremental Models

Incremental models process **only new or changed data**, improving performance for large datasets.

```sql
{{ config(materialized='incremental') }}
```

---

## Deployment and Orchestration

dbt projects can be deployed using:

* **dbt Cloud**
* **Airflow**
* **CI/CD pipelines**
* **GitHub workflows**

This allows automated data transformation workflows.
