# INSTRUCTIONS BEFORE ARRIVAL

Please complete these steps before the course starts.
The goal is to spend Day 1 learning, not debugging installations.

If you get stuck, contact:
`romain.sacchi@psi.ch`

## Minimum hardware

- Minimum: `8 GB` RAM
- Preferred: `16 GB` RAM

## What these tools are for

- `Git`: downloads and updates this course repository.
- `Conda`: installs Python packages in an isolated environment.
- `Jupyter Lab`: runs the tutorial notebooks.

## 1) Install Git and Conda

Install:
- Git: https://git-scm.com/downloads
- Anaconda: https://www.anaconda.com/products/distribution

Mac (with Homebrew) example for Git:

```bash
brew install git
```

Check that both tools are available:

```bash
git --version
conda --version
```

If `conda` is not found, close and reopen your terminal, then try again.

## 2) Open a terminal and understand your location

These commands help you navigate folders:

```bash
pwd        # shows your current folder
ls         # lists files/folders in the current folder
cd ..      # go one level up
cd <name>  # go into folder <name>
```

Example: go to `Documents` before cloning:

```bash
cd Documents
```

## 3) Clone this repository

You have two options:

- Option A (GUI): GitHub Desktop https://desktop.github.com/download/
- Option B (terminal): use `git clone`

Terminal example:

```bash
git clone <repository-url>
cd barcelona-regionalized-lcia
```

`git clone` creates a local copy of the course material on your computer.

## 4) Create the course environment (`bw2`)

From the repository root, go to `envs`:

```bash
cd envs
```

Choose one command:

- Mac Apple Silicon (M1/M2/M3/M4):

```bash
conda env create -f bw2_env_osxARM.yaml
```

- Windows or Mac Intel:

```bash
conda env create -f bw2_env_win64.yaml
```

Then verify that the environment exists:

```bash
conda env list
```

You should see `bw2` in the list.

## 5) Activate `bw2` and run a quick check

Activate:

```bash
conda activate bw2
```

Quick checks:

```bash
python --version
python -c "import bw2data, bw2calc, bw2io; print('Brightway core import: OK')"
```

## 6) Prepare the BAFU:2025 inventory file

This course uses the **BAFU:2025** open-access LCA database as a
Brightway-compatible Excel inventory file.

Database page:
- https://nexus.openlca.org/database/BAFU

Place the Excel inventory file in:
- `tutorials/DAY 1/assets/`

Recommended filename:
- `BAFU_2025_inventory.xlsx`

The actual Brightway import is done during Day 1 in:
- `tutorials/DAY 1/D1-04 First LCA from demand to score in Brightway.ipynb`

## 7) Launch Jupyter Lab and run setup notebook

From the repository root:

```bash
jupyter lab
```

Then open and run all cells in:

- `tutorials/00_SETUP/00 - Setup and First Checks.ipynb`

## 8) Terms of use and citation requirements (BAFU:2025)

The Swiss Federal Administration provides its eco-inventory data free of charge and with few restrictions.
Anyone wishing to use the data must first accept the terms of use.

Requirements:
- The data may not be resold.
- The source of the data must be cited as:
  `Database of the Swiss Federal Administration, FOEN:20XY, Federal Office for the Environment, 2025.`
- The Swiss Federal Administration cannot be held responsible for the published data.
- It is recommended that specialists be consulted for the implementation of life cycle assessments and the analysis of the results.

## 9) If something fails, email this information

Send to `romain.sacchi@psi.ch`:

- Operating system and chip type (`Windows`, `Mac Intel`, `Mac Apple Silicon`)
- Output of `conda env list`
- Output of `python --version`
- Full error message from terminal or notebook
