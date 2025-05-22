# Data Engineer Take Home

Welcome! This document contains the take home assessment for data engineer candidates at First Resonance

## Take Home Evaluation

### Overview

This test simulates a data pipeline where your application will ingest data from an API, load into a database, and transform the data into more consumable datasets (or data marts). 

### Evaluation

#### Technical:

- Coding Proficiency
  - Most of our data-pipeline tasks involve writing code, and we expect you to be comfortable doing this frequently. Please provide code that is clear, well-annotated, understandable.

- System Integration
  - Writing code is only one piece of deploying a production service. Through this assignment, we want to see how you approach the full deployment lifecycle. Since this is a practical exercise, we encourage you to complete what you can in the solution itself and outline any additional production considerations in your documentation.

#### Non-Technical:

- Requirement Analysis
  - Data ingestion requests can arrive with varying degrees of detail. We’ll look at how well you interpret and address these requirements in your solution.

- Simplicity
  - Can others easily follow your reasoning? Did you arrive at your solution using a direct, uncomplicated approach, avoiding unnecessary complexity?

- Documentation
  - Is your solution clearly explained? We’ll review whether the accompanying information and data make it easy to understand how everything fits together.

You will asked to present or discuss some of this work during your onsite interview

## Guidelines

* Please time-box the exercise to a few hours only
* If you need any help or clarification, please reach out to the First Resonance team.
* As you proceed, use a Git repository to host all your files.
* Submit your results as a zipped file. Please send this to First Resonance (the recruiter you're working with). Do not post your git repo publicly anywhere on the internet.
* We expect your solution to contain all the instructions to reproduce your environment

---

## Project Milestones

### Project Objective

Build a robust, scalable data pipeline using modern data engineering tooling. This pipeline will extract data from a public API, store it in a relational database, transform it using dbt, and expose critical datasets for analytical use. You are expected to go beyond implementation and make thoughtful design decisions around architecture, monitoring, CI/CD, and documentation.

### Part 0: Environment Setup

- Define a `docker-compose.yml` with:
  - A Postgres database container
  - An Airflow container
  - A dbt container (or use dbt within Airflow)
- Implement a Makefile or shell script to stand up the environment with one command.
- Configure environment variables securely via `.env` and Docker secrets.


### Part I: Data Ingestion

- Create a modular and parameterized Airflow DAG to extract data from the SpaceX Launches API:
  - [SpaceX API Launch Data](https://api.spacexdata.com/v4/launches)
  - [API Documentation](https://github.com/r-spacex/SpaceX-API/blob/master/docs/launches/v4/all.md)
- Load the data incrementally into a well-modeled Postgres schema.
- Implement:
  - Retry logic and failure notifications (Slack/email)
  - Metadata tracking (e.g., `ingestion_log` table)
  - Basic data quality checks using Great Expectations or similar


### Part II: Data Transformation

- Use dbt models to create curated datasets:
  1. **Failed Launches Dataset** – counts, reasons, categorized by year, rocket type, etc.
  2. **Dragon Missions Dataset** – launch details including crew, mission duration, outcome.
- Apply:
  - Modular dbt folder structure (seed, staging, mart layers)
  - dbt tests for nulls, uniqueness, referential integrity
  - Documentation using `dbt docs`

### Part III: Deployment & CI/CD

- Configure a CI/CD pipeline using GitHub Actions (or similar) to:
  - Run linting and config validation
  - Run dbt tests
  - Deploy DAGs and models
- Briefly explain your approach to:
  - Secrets management
  - Secure connection handling

### Part IV: Documentation & Architecture

Include a detailed `README.md` or `docs/` folder with:

1. **Setup Instructions**
   - Environment installation and launch
2. **System Architecture**
   - Diagram and narrative of services and data flow
3. **Design Justifications**
   - Schema design, DAG structure, transformation logic
4. **Scaling Plan**
   - Approach for scaling to 10x or 100x data
   - Suggestions for versioning or data lake integrations

---

### References 

- [Running Airflow Locally](https://airflow.apache.org/docs/apache-airflow/2.3.0/start/local.html)
- [How Airflow + dbt Work Together](https://www.getdbt.com/blog/dbt-airflow)
- [Orchestrating dbt with Airflow](https://rasiksuhail.medium.com/orchestrating-dbt-with-airflow-a-step-by-step-guide-to-automating-data-pipelines-part-i-7a6db8ebc974)
- [Data warehouse tech stack with PostgreSQL, DBT, Airflow](https://medium.com/@smlalene/data-warehouse-tech-stack-with-postgresql-dbt-airflow-35dfb7e743f8)

## Notes/Considerations

- There are many ways to complete these tasks. You are encouraged to determine the best solution and justify this approach in your documentation.
- Additional coding best practices (testing, error handling, etc) are optional but recommended.
