# Regionalised LCIA Course (Barcelona 2026)

![Sagrada Familia in Barcelona](_images/Sagrada_Família._Façana_del_Naixement.jpg)

## Course Overview

This repository contains all material for the 3-day course:
**Regionalised LCIA for Beginner and Intermediate Brightway users**.

The core course focuses on:
- Brightway 2.5 foundations
- Regionalised LCIA with Edges
- Scenario-based LCIA
- Inventory flow assessment

The format mixes short lectures and hands-on notebook sessions.
All material remains available after the course.

## Learning Outcomes

By the end of the course, participants will be able to:
- Explain Brightway's architecture and matrix-based LCA computation flow.
- Build and run LCA models in Python.
- Perform uncertainty analysis and contribution analysis.
- Import and analyze a national LCA inventory database from Excel.
- Run regionalised LCIA workflows with Edges.
- Implement scenario-based LCIA with parameterised characterization factors.
- Perform inventory flow assessment and interpret supply-chain criticality signals.

## Target Audience

- LCA practitioners with beginner or intermediate Python skills.
- No prior Brightway experience required.
- Participants should already know core LCA concepts.

## Database Used in the Course

This course uses the **BAFU:2025** LCA database (open access), provided by the
Swiss Federal Office for the Environment (FOEN) as a Brightway-compatible Excel inventory file.

Database page:
- https://nexus.openlca.org/database/BAFU

## Terms of Use (BAFU:2025)

The Swiss Federal Administration provides its eco-inventory data free of charge and with few restrictions.
Anyone wishing to use the data must first accept the terms of use.

Requirements:
- The data may not be resold.
- The source of the data must be cited as:
  `Database of the Swiss Federal Administration, FOEN:20XY, Federal Office for the Environment, 2025.`
- The Swiss Federal Administration cannot be held responsible for the published data.
- It is recommended that specialists be consulted for the implementation of life cycle assessments and the analysis of the results.

## Repository Structure

- [tutorials/00_SETUP/](tutorials/00_SETUP/README.MD): pre-course setup and first checks
- [tutorials/DAY 1/](tutorials/DAY%201/README.MD): Brightway foundations + BAFU Excel import
- [tutorials/DAY 2/](tutorials/DAY%202/README.MD): regionalised LCIA with Edges
- [tutorials/DAY 3/](tutorials/DAY%203/README.MD): scenario LCIA and inventory flow assessment

## Day-by-Day Notebooks

See the detailed agenda with notebook mapping in [SCHEDULE.MD](SCHEDULE.MD).

## Before the Course

Follow [INSTRUCTIONS.MD](INSTRUCTIONS.MD) and complete:
- `tutorials/00_SETUP/00 - Setup and First Checks.ipynb`

## Software

Core environment files are in `envs/`:
- `bw2_env_osxARM.yaml` or `bw2_env_win64.yaml`

## Teaching Staff

- Instructor: Romain Sacchi, Paul Scherrer Institute (PSI)
- Location: Barcelona, Spring 2026
- Format: lectures + hands-on workshops

## License

Unless otherwise specified, material in this repository is licensed under
BSD 3-Clause. See [LICENSE.md](LICENSE.md).
