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

You may be asked to present or discuss some of this work during your onsite interview

## Guidelines

* Please time-box the exercise to a few hours only
* If you need any help or clarification, please reach out to the First Resonance team.
* As you proceed, use a Git repository to host all your files.
* Submit your results as a [Git Bundle](https://utappia.org/2015/04/27/git-bundle-backup/) or a zipped file. Please send this to First Resonance (the recruiter you're working with). Do not post your git repo publicly anywhere on the internet.
* We expect your solution to contain all the instructions to reproduce your environment

## Project Milestones

### Part 0: Setup your containerized environment

docker-compose file to specify two services
- a Postgres database container
- an Airflow container

### Part I: Extract and Load Data

Write an Airflow DAG to extract data from the API endpoint provided and load into the postgres database:

[SpaceX API Launch Data](https://api.spacexdata.com/v4/launches)

Documentation on this endpoint can be found [here](https://github.com/r-spacex/SpaceX-API/blob/master/docs/launches/v4/all.md)

Take care to adhere to clean coding principles and follow usual best practices, especially with regard to code readability. 

Be sure to incorporate database design and data modeling practices as you load data into the database.

### Part II: Transform data

Use dbt in a separate Airflow DAG to transform data into consumable datasets. We recommend two datasets related to (1) failed launches (count, reasons, etc) and (2) launches related to the Dragon vehicle (launches with crew members). These should be structured in a way that is consumable to business/operational groups (i.e. compiled, stand-alone datasets versus lots of joins/unions)

### Part III: Documentation

Add the following documentation to the `README` file:

1. Explain how to run the code and the setup you documented in parts I and II.
2. Include any packaging steps we may need to follow.
3. Explain your approach to data modeling and transformation

Include all of the above documentation, including the `README`, along with all of your code in a git bundle that you send back to us.

### References 

- [Running Airflow Locally](https://airflow.apache.org/docs/apache-airflow/2.3.0/start/local.html)
- [How Airflow + dbt Work Together](https://www.getdbt.com/blog/dbt-airflow)
- [Orchestrating dbt with Airflow](https://rasiksuhail.medium.com/orchestrating-dbt-with-airflow-a-step-by-step-guide-to-automating-data-pipelines-part-i-7a6db8ebc974)
- [Data warehouse tech stack with PostgreSQL, DBT, Airflow](https://medium.com/@smlalene/data-warehouse-tech-stack-with-postgresql-dbt-airflow-35dfb7e743f8)

## Notes/Considerations

- There are many ways to complete these tasks. You are encouraged to determine the best solution and justify this approach in your documentation.
- Additional coding best practices (testing, error handling, etc) are optional but recommended.
