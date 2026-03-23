# Repository Guide For Agents

This repository is course material for the 3-day "Regionalised LCIA Course (Barcelona 2026)".
Most work here is content maintenance, not application development.

## What Lives Here

- `README.MD`: course overview, learning outcomes, repository map.
- `INSTRUCTIONS.MD`: pre-arrival setup steps for participants.
- `SCHEDULE.MD`: day-by-day agenda mapped to notebooks.
- `READING_MATERIAL.md`: pre-course reading list.
- `HOME_ASSIGNMENT.md`: optional post-course assignment.
- `envs/`: conda environments. The main teaching environment is `bw`.
- `tutorials/00_SETUP/`: pre-course setup notebook.
- `data/`: bundled course data, including the BAFU workbook used on Day 1.
- `tutorials/DAY 1/`: Brightway foundations, BAFU import, and an `ecoinvent` import overview.
- `tutorials/DAY 2/`: regionalised LCIA with `edges`.
- `tutorials/DAY 3/`: scenario LCIA and inventory flow assessment.

## Course Flow

Participants are expected to:

1. Read `INSTRUCTIONS.MD`.
2. Build the `bw` conda environment from `envs/`.
3. Run `tutorials/00_SETUP/00 - Setup and First Checks.ipynb`.
4. Work through Day 1, Day 2, then Day 3 notebooks in schedule order.

The schedule, notebook names, and tutorial README files should stay aligned.

## Notebook Editing Guidance

- Preserve the current teaching pattern when possible:
  title, learning goals, concept/workflow, exercise, then a minimal answer/template cell.
- Keep notebooks free of stored outputs unless the user explicitly asks for committed outputs.
- Prefer small, surgical notebook edits. Do not rewrite notebook metadata unless necessary.
- If notebook files are renamed, update links in `README.MD`, `SCHEDULE.MD`, and the day-level `README.MD`.
- Day 2 and Day 3 currently mix concept text with lightweight scaffold exercises; keep that distinction clear if expanding them.

## Data And Assets

- Day 1 uses the bundled file `data/lci-bafu.xlsx`.
- The BAFU website link is for reference and terms of use; participants do not download it during the course.
- `ecoinvent` is discussed for users who work with it, but it is not included in this repository and is not used in the hands-on course because of licensing constraints.
- Exercise assets for later days live under each day's `assets/` folder and are safe to reference in notebooks.

## Environment Files

- `envs/bw_env_osxARM.yaml` and `envs/bw_env_win64.yaml` define the main course environment.
- Other environment files (`premise`, `odym`, `wurst`) appear auxiliary; avoid changing them unless the task explicitly involves those tools.
- If changing core package guidance, keep top-level setup instructions consistent with the relevant environment file.

## Practical Cautions

- This repo may contain local-only files such as `.DS_Store`, `.idea/`, and this `AGENTS.md`.
- Treat the repository as teaching material first: clarity, reproducibility, and stable notebook links matter more than clever refactors.
