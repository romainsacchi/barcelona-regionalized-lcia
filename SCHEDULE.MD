# Course Schedule

The schedule below maps each time block to specific notebooks.
Break durations and time can be adjusted during the course.

## PRIOR TO ARRIVAL

Complete:
- [INSTRUCTIONS.MD](INSTRUCTIONS.MD)
- [tutorials/00_SETUP/00 - Setup and First Checks.ipynb](tutorials/00_SETUP/00%20-%20Setup%20and%20First%20Checks.ipynb)
- check [reading material](READING_MATERIAL.md)

## How to open the jupyter notebooks listed below
 - open your shell (terminal for Mac users, miniforge for Windows users)
   ```bash
   conda activate bw
   jupyter lab
 - open the notebook we are working on


## DAY 1 (Wednesday, May 27, 2026) - `brightway` Foundations

### 09:00 - 09:30
Welcome, setup check, course roadmap
- [D1-01 Python and Jupyter minimum refresher](tutorials/DAY%201/D1-01%20Python%20and%20Jupyter%20minimum%20refresher.ipynb)

### 09:30 - 10:30
`brightway` architecture and core data model
- [D1-02 `brightway` architecture and data model](tutorials/DAY%201/D1-02%20Brightway%20architecture%20and%20data%20model.ipynb)

### 10:30 - 11:00
Coffee break

### 11:00 - 13:00
Manual matrix LCA, `brightway` first LCA, BAFU:2025 import, and `ecoinvent` import overview
- [D1-03 Manual LCA with `numpy` matrices - Heijungs and Suh 2002 vs `brightway`](tutorials/DAY%201/D1-03%20Manual%20LCA%20with%20NumPy%20matrices%20-%20Heijungs%20and%20Suh%202002%20vs%20Brightway.ipynb)
- [D1-04 First LCA from demand to score in `brightway`](tutorials/DAY%201/D1-04%20First%20LCA%20from%20demand%20to%20score%20in%20Brightway.ipynb)

### 13:00 - 15:00
Lunch break

### 15:00 - 16:30
Uncertainty and Monte Carlo
- [D1-05 Uncertainty and Monte Carlo basics](tutorials/DAY%201/D1-05%20Uncertainty%20and%20Monte%20Carlo%20basics.ipynb)

### 16:30 - 17:00
Coffee break

### 17:00 - 19:00
Data QA/linking workflow and contribution analysis
- [D1-06 Data quality checks and linking workflow](tutorials/DAY%201/D1-06%20Data%20quality%20checks%20and%20linking%20workflow.ipynb)
- [D1-07 Contribution analysis and result visualization](tutorials/DAY%201/D1-07%20Contribution%20analysis%20and%20result%20visualization.ipynb)

## DAY 2 (Thursday, May 28, 2026) - Regionalised LCIA

### 09:00 - 10:00
Day 1 recap and environment checks
- [D2-01 Day 1 recap and readiness checks](tutorials/DAY%202/D2-01%20Day%201%20recap%20and%20readiness%20checks.ipynb)

### 10:00 - 11:00
`edges` fundamentals
- [D2-02 `edges` fundamentals and regionalisation concepts](tutorials/DAY%202/D2-02%20Edges%20fundamentals%20and%20regionalisation%20concepts.ipynb)

### 11:00 - 11:15
Coffee break

### 11:15 - 13:00
`edges` workflow, spatial matching, and regionalised methods
- [D2-03 Introduction to `edges` workflow and API](tutorials/DAY%202/D2-03%20Introduction%20to%20edges%20workflow%20and%20API.ipynb)
- [D2-04 Spatial matching and fallback logic](tutorials/DAY%202/D2-04%20Spatial%20matching%20and%20fallback%20logic.ipynb)
- [D2-05 Regionalised methods across impact categories](tutorials/DAY%202/D2-05%20Regionalised%20methods%20across%20impact%20categories.ipynb)

### 13:00 - 15:00
Lunch break

### 15:00 - 16:30
Variability and uncertainty in regionalised LCIA
- [D2-06 Variability and uncertainty in regionalised LCIA](tutorials/DAY%202/D2-06%20Variability%20and%20uncertainty%20in%20regionalised%20LCIA.ipynb)

### 16:30 - 17:00
Coffee break

### 17:00 - 19:00
Case study: regionalised hydrogen pathways
- [D2-07 Case study - Regionalised hydrogen pathways](tutorials/DAY%202/D2-07%20Case%20study%20-%20Regionalised%20hydrogen%20pathways.ipynb)

## DAY 3 (Friday, May 29, 2026) - Scenario LCIA and Inventory Flow Assessment

### 09:00 - 10:00
Day 2 recap and Day 3 readiness checks
- [D3-01 Day 2 recap and Day 3 readiness checks](tutorials/DAY%203/D3-01%20Day%202%20recap%20and%20Day%203%20readiness%20checks.ipynb)

### 10:00 - 11:00
Scenario-based LCIA with parameterised CFs
- [D3-02 Parameterised characterization factors with edges](tutorials/DAY%203/D3-02%20Parameterised%20characterization%20factors%20with%20edges.ipynb)
- [D3-03 Time and scenario integration workflow](tutorials/DAY%203/D3-03%20Time%20and%20scenario%20integration%20workflow.ipynb)

### 11:00 - 11:15
Coffee break

### 11:15 - 12:15
Scenario-based LCIA with parameterised CFs
- [D3-02 Parameterised characterization factors with edges](tutorials/DAY%203/D3-02%20Parameterised%20characterization%20factors%20with%20edges.ipynb)
- [D3-03 Time and scenario integration workflow](tutorials/DAY%203/D3-03%20Time%20and%20scenario%20integration%20workflow.ipynb)

### 12:15 - 13:00
Inventory flow assessment I
- [D3-04 Inventory flow assessment I - tracing intermediates](tutorials/DAY%203/D3-04%20Inventory%20flow%20assessment%20I%20-%20tracing%20intermediates.ipynb)

### 13:00 - 15:00
Lunch break

### 15:00 - 16:00
Inventory flow assessment II
- [D3-05 Inventory flow assessment II - criticality factors](tutorials/DAY%203/D3-05%20Inventory%20flow%20assessment%20II%20-%20criticality%20factors.ipynb)

### 16:00 - 16:15
Coffee break

### 16:15 - 19:00
Capstone dual case study and wrap-up
- [D3-06 Capstone dual case study](tutorials/DAY%203/D3-06%20Capstone%20dual%20case%20study.ipynb)
