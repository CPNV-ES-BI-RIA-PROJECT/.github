# CPNV-ES-BI-RIA-PROJECT


<img width="1324" height="892" alt="image" src="https://github.com/user-attachments/assets/c40fda8e-6d4c-4e04-9011-49ffc5e9bc22" />


# Sprint 001

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

    2 weeks — Review and retro scheduled for Friday, March 5, 2026.
