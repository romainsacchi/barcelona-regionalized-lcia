# Notebook Refinement Design Memo

Status:
- Derived from `NOTEBOOK_REFINEMENT_QUESTIONNAIRE.md`
- Stable enough to guide Setup and Day 1 revisions immediately
- Day 2 has strong high-level constraints, but most notebook-specific decisions are still open

## 1. Core Teaching Direction

### Audience

- LCA practitioners with little or no `brightway` experience
- Beginner-to-intermediate Python level
- Comfortable with LCA concepts, but mostly from GUI tools or Excel
- Priority audience: researchers and consultants

### Primary outcomes

Participants should leave able to:
- handle databases in `brightway`
- model activities and exchanges
- run LCAs and interpret results
- run regionalised LCIA with `edges`

### Pedagogical style

- Roughly `20%` lecture, `80%` hands-on
- Notebooks should be mostly scaffolded exercises, not fully worked demos
- Hidden solution cells should be used throughout
- Use short checkpoint tasks every 10-20 minutes
- Optimize for live teaching by instructors
- Favor coding tasks, with some interpretation questions
- Use a consistent notebook template across all days

### Standard notebook template

Each notebook should generally include:
- title and short framing paragraph
- learning objectives at the top
- background reference(s), in APA style
- concept / workflow sections
- short checkpoint tasks during the notebook
- hidden solution cells
- a short recap at the end

### Cross-cutting conventions

- Use attributional modeling language throughout
- Standardize terminology:
  - `activity` for processes
  - `exchange` for flows between activities
  - `characterization factor` for impact per unit of flow
- Revisit repeatedly:
  - activities vs exchanges
  - inventory vs impact assessment
  - variability vs uncertainty

### Preferred outputs

- scalar scores
- contribution plots
- uncertainty distributions
- traceability outputs

Preferred visuals:
- stacked bars
- contribution plots
- histograms / boxplots
- maps only where useful on Day 2

## 2. Example Strategy

### Examples to prioritize

- power plants / electricity production
- passenger car transport
- possibly agriculture or waste if well represented

### Continuity strategy

- Use several separate examples by topic
- Reuse a few activities/flows across notebooks for continuity
- A battery-electric car can act as a loose cross-day case

### First-LCA activity guidance

- Avoid empty or near-empty activities
- For the first concrete Brightway LCA, a coal-fired power plant is acceptable
- Gasoline-fueled passenger car transport is a preferred teaching example in general

### Geographic direction

- Start with Switzerland-centered BAFU examples if needed
- Move toward Spain / Mediterranean / broader regional comparisons as early as practical

### BAFU vs ecoinvent

- BAFU is the actual hands-on course database
- `ecoinvent` should appear in a dedicated section inside `D1-04`
- That section should include pseudocode / commented code
- It should mention the specific `bw2io` importers, but should not be run live
- The comparison should stay brief

## 3. Libraries And APIs To Expose

Explicitly teach these packages by name:
- `bw2data`
- `bw2io`
- `bw2calc`
- `bw2analyzer`

Key operations students should see in code:
- create / activate / delete projects
- select and inspect databases
- rename databases
- find activities
- inspect exchanges
- run LCAs
- run Monte Carlo analysis

Visualization / interpretation tools:
- `matplotlib`
- `polyviz` where contribution analysis benefits from it

## 4. References Strategy

### Anchor references

- Day 1:
  - Mutel (2017)
  - Heijungs and Suh (2002)
- Day 2:
  - Sacchi et al. (2025)
  - Seitfudem et al. (2025)
- Day 3:
  - Watanabe and Cherubini (2026)
  - Scherer et al. (2023)
  - Koyamparambath et al. (2024)

### Reference policy

- Every notebook should include at least one relevant reference
- References should be background reading, not line-by-line methodological justification
- Use APA-style citations in notebooks
- Prefer one anchor paper plus a small supporting set

## 5. Setup Notebook Design

Notebook:
- `tutorials/00_SETUP/00 - Setup and First Checks.ipynb`

### Required changes

- Strengthen environment diagnosis
- Verify imports beyond core `brightway`, including `edges`
- Check for presence of `data/lci-bafu.xlsx`
- Add a small kernel / notebook-use micro-tutorial
- Add troubleshooting for common failures:
  - missing dependencies
  - missing sparse solver support
  - inactive / wrong Python environment

### Important note

- The notebook does not need a deep path tutorial
- File-size validation for `data/lci-bafu.xlsx` is optional, not mandatory

## 6. Day 1 Narrative

### Story

Day 1 should build confidence by doing:
- warm up Python/Jupyter
- explain `brightway` architecture with simple structures
- connect LCA mathematics to matrices manually
- import a real database into `brightway`
- run first LCAs
- introduce uncertainty and contribution analysis on real data

### Mandatory Day 1 outcomes before Day 2

Students must be able to:
- activate and use projects
- select databases
- find activities
- run an LCA
- understand activities vs exchanges
- understand the `brightway` data model well enough to follow `edges`

## 7. Day 1 Notebook Specifications

### D1-01 Python and Jupyter minimum refresher

Role:
- confidence warm-up
- filter setup issues

Scope:
- variables
- lists
- loops
- functions
- dictionaries
- LCA-flavored examples

Avoid:
- classes
- decorators
- context managers
- advanced pandas

Teaching notes:
- target about 30 minutes
- use "try it yourself" prompts rather than formal exercises

### D1-02 Brightway architecture and data model

Role:
- make the data model visible before the real import

Must show in code:
- projects
- databases
- activities
- exchanges
- methods
- how they relate to each other

Approach:
- use toy examples, not BAFU yet
- a small toy exercise is acceptable if it helps students inspect an activity or exchange

Anchor reference:
- Mutel (2017)

### D1-03 Manual LCA with NumPy matrices

Role:
- make the computational structure of LCA explicit
- build the bridge to what `brightway` does under the hood

Approach:
- be rigorous with notation
- stay close to Heijungs and Suh notation
- keep examples abstract, not domain-specific
- use 2-3 tiny systems at most

Must show:
- technosphere matrix construction
- biosphere matrix construction
- demand vector
- matrix solve
- characterization step
- matrix multiplication / inversion / element-wise multiplication

Exercise design:
- students construct matrices and demand for a simple system
- solve manually
- compare with the expected computation flow

Important clarification:
- do not use `brightway` directly in this notebook
- manually recreate the workflow `brightway` uses

### D1-04 First LCA from demand to score in Brightway

Role:
- main practical milestone of Day 1

Must emphasize:
- project setup
- BAFU import mechanics
- database inspection
- first score calculation

Students should understand explicitly:
- `ExcelImporter`
- strategies
- biosphere matching
- statistics
- unlinked exchanges
- database writing

Should include:
- immediate inspection of the imported database
- a dedicated `ecoinvent` import overview section
- a brief troubleshooting section

Example choice:
- use a coal-fired power plant rather than a random activity if possible

Important note:
- `D1-06` becomes the deeper data-debugging notebook, so `D1-04` should not become too heavy on error-resolution detail

### D1-05 Uncertainty and Monte Carlo basics

Role:
- practitioner-ready Monte Carlo workflow, not just concepts

Approach:
- use BAFU uncertainty definitions directly
- keep conceptual intro brief
- move quickly into actual `brightway` usage

Must show:
- uncertainty distributions on exchanges
- `stats_arrays` context
- `bw2calc.LCA(..., use_distributions=True)` style workflow
- score distributions
- confidence intervals
- percentiles

Exercise:
- compare two activities, such as coal vs gas power
- interpret overlap in score distributions
- identify what drives uncertainty

Key lesson:
- overlapping intervals weaken simple ranking claims

### D1-06 Data quality checks and linking workflow

Role:
- realistic foreground import debugging against BAFU

Direction:
- move away from synthetic CSV-only checks
- use realistic foreground inventory files supplied by the instructor
- focus on import errors that block correct linking

Must cover:
- unlinked technosphere exchanges
- unlinked biosphere exchanges
- spelling / naming problems
- units
- categories
- duplicate codes
- migration files

Priority:
- do not overemphasize `pandas`
- focus on import logic and debugging workflow

Reference source:
- reuse structure from the PSI winter school Brightway notebook where helpful

### D1-07 Contribution analysis and result visualization

Role:
- show which activities and emissions drive scores
- prepare the transition to Day 2

Preferred outputs:
- top activities
- top emissions
- Sankey-like structure
- stacked bars

Possible tools:
- `matplotlib`
- `polyviz`

Dataset use:
- either use the same activity as in `D1-05`
- or use a strong BAFU example that supports the Day 2 transition

Exercise goal:
- determine foreground vs background shares
- identify main contributors
- start asking whether contribution patterns vary regionally

## 8. Day 2 Provisional Design Constraints

Day 2 notebook-specific decisions are still mostly unanswered in the questionnaire.
However, the following design constraints are already fixed enough to guide planning.

### Day 2 thematic direction

- Regionalised LCIA should extend standard Brightway practice in a concrete way
- Spain / Mediterranean examples are desirable if supported by data
- The teaching should move beyond Switzerland as early as practical
- Day 2 should likely prioritize the exchange-based / contextual logic behind `edges`
- Water scarcity is already a clear anchor topic because AWARE2.0 was explicitly selected

### Day 2 references

- Sacchi et al. (2025) should anchor the `edges` / contextual LCIA framing
- Seitfudem et al. (2025) should anchor water scarcity regionalisation
- Bulle et al. (2019) should remain a background regionalised-LCIA reference

### Day 2 outputs

- emphasize scalar results plus interpretable visuals
- maps are useful if they add real value, but are not required everywhere

### Day 2 likely examples

- electricity production remains a strong candidate
- Spanish or Mediterranean regional cases are desirable
- continuity with Day 1 examples is useful, but Day 2 can introduce new regionalised cases

## 9. What Is Ready Now

Ready for concrete notebook revision:
- Setup notebook
- all Day 1 notebooks
- top-level alignment of references, template, and exercise style

Not yet fully specified:
- Day 2 notebook-by-notebook structure
- exact `edges` APIs / functions to expose
- Day 2 exercise placement and scope
- category prioritization within Day 2

## 10. Recommended Next Revision Order

1. Setup notebook
2. `D1-04` BAFU import + `ecoinvent` overview
3. `D1-02` architecture and data model
4. `D1-03` manual matrix LCA
5. `D1-05` Monte Carlo
6. `D1-06` import debugging
7. `D1-07` contribution analysis
8. `D1-01` refresher cleanup

## 11. Immediate Open Questions Before Day 2 Rewrites

These are the minimum missing decisions that would unlock precise Day 2 notebook rewriting:
- What is the Day 2 narrative arc?
- Which impact categories are mandatory?
- Which `edges` APIs should appear in code?
- How deep should spatial matching internals go?
- How should Day 2 uncertainty differ from Day 1 uncertainty?
- What exact deliverable should the electricity case study produce?
