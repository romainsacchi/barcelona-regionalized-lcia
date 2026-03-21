# Regionalised LCIA Course (Barcelona 2026)

![Sagrada Familia in Barcelona](_images/sagrada-familia.jpg)

## Course Overview

Welcome! This repository contains all material for the 3-day course:
**Regionalised LCIA for Beginner and Intermediate `brightway` users**.

The core course focuses on:
- `brightway` 2.5 foundations
- Regionalised LCIA with `edges`
- Scenario-based LCIA
- Inventory flow assessment

The format mixes short lectures and hands-on notebook sessions.
All material remains available after the course.

## Learning Outcomes

By the end of the course, participants will be able to:
- Explain `brightway`'s architecture and matrix-based LCA computation flow.
- Build and run LCA models in Python.
- Perform uncertainty analysis and contribution analysis.
- Import and analyze a national LCA inventory database from Excel, and understand how a similar import workflow applies to `ecoinvent`.
- Run regionalised LCIA workflows with `edges`.
- Implement scenario-based LCIA with parameterised characterization factors.
- Perform inventory flow assessment and interpret supply-chain criticality signals.

## Target Audience

- LCA practitioners with beginner or intermediate Python skills.
- No prior `brightway` experience required.
- Participants should already know core LCA concepts.

## Database Used in the Course

This course uses the **BAFU:2025** LCA database (open access), provided by the
Swiss Federal Office for the Environment (FOEN) as a `brightway`-compatible Excel inventory file.

The Brightway-compatible Excel file used during the course is already included in this repository:
- `data/lci-bafu.xlsx`

Participants do **not** need to download the database before the course.
On Day 1, participants will import the bundled BAFU file into `brightway`.

We will also explain how to import the `ecoinvent` LCA database for participants who work with it.
However, `ecoinvent` is **not** included in this repository and is **not** used in the course exercises because of licensing constraints.

Database page:
- https://nexus.openlca.org/database/BAFU (reference and terms-of-use page)

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

- `data/`: bundled course data, including the BAFU Excel inventory used on Day 1
- [tutorials/00_SETUP/](tutorials/00_SETUP/README.MD): pre-course setup and first checks
- [tutorials/DAY 1/](tutorials/DAY%201/README.MD): `brightway` foundations + BAFU import + `ecoinvent` import overview
- [tutorials/DAY 2/](tutorials/DAY%202/README.MD): regionalised LCIA with `edges`
- [tutorials/DAY 3/](tutorials/DAY%203/README.MD): scenario LCIA and inventory flow assessment

## Day-by-Day Notebooks

See the detailed agenda with notebook mapping in [SCHEDULE.MD](SCHEDULE.MD).

## Before the Course

Follow [INSTRUCTIONS.MD](INSTRUCTIONS.MD) and complete:
- `tutorials/00_SETUP/00 - Setup and First Checks.ipynb`

No database download is required before arrival; the BAFU workbook is already included under `data/`.

## Software

Core environment files are in `envs/`:
- `bw_env_win64.yaml` (for Windows computers) or `bw_env_osxARM.yaml` (for Mac computers with Apple Silicon chips)

## Teaching Staff

- Instructors: 
  - [Romain Sacchi](mailto:romain.sacchi@psi.ch), Paul Scherrer Institute (PSI)
  - [Miguel Astudillo](mailto:miguel.astudillo@2-0-LCA.com), 2-0 LCA
- Location: ILCA, Barcelona, Spring 2026
- Format: lectures + hands-on workshops

## License

Unless otherwise specified, material in this repository is licensed under
BSD 3-Clause. See [LICENSE.md](LICENSE.md).
