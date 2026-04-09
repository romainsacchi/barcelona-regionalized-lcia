# INSTRUCTIONS BEFORE ARRIVAL

Please complete these steps before the course starts.
The goal is to spend Day 1 learning, not debugging installations.

If you get stuck, contact:
`romain.sacchi@psi.ch`

## Minimum hardware

- Minimum: `8 GB` RAM
- Preferred: `16 GB` RAM

## Before you start

- A stable internet connection is needed to install Git, Miniforge, and the Python packages in the `bw` environment.
- On Day 1, the notebooks also download a prepared Brightway project archive the first time it is installed into your local Brightway workspace.
- No separate database download is required for the course BAFU workbook; `data/lci-bafu.xlsx` is already bundled in this repository.

## What these tools are for

- `Git`: downloads and updates this course repository.
- `Miniforge` / `conda`: installs Python packages in an isolated environment.
- `Jupyter Lab`: runs the tutorial notebooks.

## If you are new to Python

If you are completely new to Python, we recommend spending a few hours on a beginner tutorial before the course.
We suggest the University of Helsinki's online tutorial, which requires no installation:

- https://programming-25.mooc.fi/part-1/1-getting-started

For this course, the `Introduction to Programming` section is sufficient.
You do not need to complete the `Advanced Course in Programming` section.

This will make the Day 1 Python and Jupyter refresher much easier to follow.

## 1) Install Git and Miniforge

Install:
- Git: https://git-scm.com/downloads
- Miniforge (official installers): https://github.com/conda-forge/miniforge/releases/latest

Mac (with Homebrew) example for Git:

```bash
brew install git
```

### Miniforge installation

Mac users:

- Open `Terminal`
- Download and run the official installer for your Mac architecture:

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-$(uname -m).sh"
bash Miniforge3-MacOSX-$(uname -m).sh
```

- Accept the prompt to initialize `conda` for your shell.

Windows users:

- Download `Miniforge3-Windows-x86_64.exe`
- Run the installer and keep the Start Menu shortcuts enabled.
- After installation, open the **Miniforge Prompt** from the Start Menu. This is the recommended shell for using `conda` on Windows.
- If possible, install Miniforge in a path without spaces or special characters.

Check that both tools are available.
On Mac, use `Terminal`.
On Windows, use `Miniforge Prompt`:

```bash
git --version
conda --version
```

If `conda` is not found:

- On Mac, close and reopen `Terminal`, then try again.
- On Windows, make sure you are in `Miniforge Prompt`. If you want to use another shell later, run `conda init`, close the shell, and reopen it.

## 2) Open a terminal and understand your location

These commands help you navigate folders:

```bash
pwd        # shows your current folder
ls         # for Mac, lists files/folders in the current folder
dir        # for Windows, lists files/folders in the current folder
cd ..      # go one level up
cd <name>  # go into folder <name>
```

Recommended shell:

- Mac: `Terminal`
- Windows: `Miniforge Prompt`

Example: go to `Documents` before cloning:

```bash
cd Documents
```

## 3) Clone this repository

You have two options:

- Option A (GUI): GitHub Desktop https://desktop.github.com/download/
- Option B (terminal): use `git clone`

At this point, you might want to create a folder containing your cloned projects. Otherwise they will be listed directly under "Documents".

```bash
mkdir GitHub
cd GitHub
```
This creates a folder named "GitHub", and you enter it with cd. 

Terminal example:

```bash
git clone https://github.com/romainsacchi/barcelona-regionalized-lcia.git
cd barcelona-regionalized-lcia
```

`git clone` creates a local copy of the course material on your computer (in the GitHub folder created above).
The repository URL above ends with `.git`, which is the standard clone URL shown on the GitHub page.

## 4) Create the course environment (`bw`)

From the repository root, go to `envs`:

```bash
cd envs
```

Choose one command:

- Mac Apple Silicon (M1/M2/M3/M4):

```bash
conda env create -f bw_env_osxARM.yaml
```

- Windows or Mac Intel:

```bash
conda env create -f bw_env_win64.yaml
```

Then verify that the environment exists:

```bash
conda env list
```

You should see `bw` in the list.

## 5) Activate `bw` and run a quick check

Activate in the same shell (`Terminal` on Mac or `Miniforge Prompt` on Windows):

```bash
conda activate bw
```

Quick checks:

```bash
python --version
python -c "import bw2data, bw2calc, bw2io; print('Brightway core import: OK')"
```

There should be no error messages, and the last line should print `Brightway core import: OK`.

### Apple Silicon note about the sparse solver warning

On Apple Silicon, `bw2calc` may print a warning about missing `scikit-umfpack`.
In this course environment, this usually means the `bw` environment drifted and
`setuptools` became too new, which breaks the legacy `scikits.umfpack` import.

If you see this warning after activating `bw`, run:

```bash
conda activate bw
conda install "setuptools<81"
```

Then verify:

```bash
python -c "import scikits.umfpack; print('UMFPACK import: OK')"
```

If the environment is still inconsistent, recreate it from the YAML file.

If a failed `conda env update` leaves imports like `bw2calc` or
`scikits.umfpack` broken, repair the packaging tools first:

```bash
conda activate bw
conda install --force-reinstall "setuptools<81" "pip<26"
```

Then retry the environment update if needed.


## 6) We will use the BAFU:2025 database imported from an inventory file

This course uses the **BAFU:2025** open-access LCA database as a
`brightway`-compatible Excel inventory file.

Database page:
- https://nexus.openlca.org/database/BAFU

The Brightway-compatible Excel file is already included in this repository:
- `data/lci-bafu.xlsx`

You do **not** need to download the database from the website above for this course.
The link is provided as a reference and for the terms of use.

The actual `brightway` import is done during Day 1 in:
- `tutorials/DAY 1/D1-04 First LCA from demand to score in Brightway.ipynb`

During Day 1, we will also show how an `ecoinvent` import workflow fits into a `brightway` setup for participants who use that database.
However, `ecoinvent` is not included in this repository and will not be used during the three-day hands-on course because of licensing constraints.

## 7) Launch Jupyter Lab and run setup notebook

From the *repository root* (you might still be in `envs/` after creating the environment, so go back up one level, using `cd ..`):

```bash
jupyter lab
```

Then open and run all cells in:

- `tutorials/00_SETUP/00 - Setup and First Checks.ipynb`

Keep the same `bw` environment for the full course.
Day 2 and Day 3 assume that the Brightway project created on Day 1 is still available.

## 8) Terms of use and citation requirements (BAFU:2025)

The Swiss Federal Administration provides its eco-inventory data free of charge and with few restrictions.
Anyone wishing to use the data must first accept the terms of use.

Requirements:
- The data may not be resold.
- The source of the data must be cited as:
  `Database of the Swiss Federal Administration, FOEN:20XY, Federal Office for the Environment, 2025.`
- The Swiss Federal Administration cannot be held responsible for the published data.
- It is recommended that specialists be consulted for the implementation of life cycle assessments and the analysis of the results.

## 9) If something fails or if you are stuck, email this information

Send to `romain.sacchi@psi.ch`:

- Operating system and chip type (`Windows`, `Mac Intel`, `Mac Apple Silicon`)
- Output of `conda env list`
- Output of `python --version`
- Full error message from terminal or notebook
