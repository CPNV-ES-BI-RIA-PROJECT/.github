# CPNV-ES-BI-RIA-PROJECT


<img width="1324" height="892" alt="image" src="https://github.com/user-attachments/assets/c40fda8e-6d4c-4e04-9011-49ffc5e9bc22" />



# Fundamental Principle of the Project

The ETL pipeline must not modify the business logic.

It must only:

* Normalize formats (ICS → JSON → SQL)
* Ensure that each event retains exactly the same attributes
* Guarantee traceability through a unique UID

## Business context – “Calendar to Invoice”

A services company (consulting / software development) wants to analyze its employees’ calendars in order to leverage worked time data within a Business Intelligence tool.

Each employee uses a calendar in ICS format to plan their daily activities. Some meetings correspond to billable work for clients, while others relate to non-billable internal activities.

The objective is not to generate invoices directly, but to:

* Extract events from ICS files.
* Transform these events into a structured format (JSON).
* Load this data into a single `events` table in a data warehouse.

The BI tool, consuming the data warehouse, will then be responsible for:

* Identifying billable events (via a `[client]` prefix in the description)
* Calculating durations
* Applying daily or hourly rates (coming from another data source)
* Producing the necessary indicators and analyses


# Sprint 000

## Goal

    Deliver an initial working version of the ELT to begin testing with business data.
    Provide OPS teams with container images to start deployment testing.

## Constraints

    No load management: one ETL instance and one microservice of each type.
    Single processing cycle: one data file to process.
    Sequential pipeline: Extract -> Transform -> Load (E -> T -> L).
    Load step must output SQL files; no direct import into the DataMart.
    No authentication.
    Internal ELT communication via REST calls (gRPC under evaluation).
    Only the API will be tested; front-end excluded.
    No cache management.

## TODO

   The definition of done Will be co-written by the teams during the sprint and applied during the next iteration.

## Sprint duration

    2 weeks — Review and retro scheduled for Thursday, March 5, 2026.

---

* [Sprint 001](./sprint001.md)
* [Spring 002](./sprint002.md)

