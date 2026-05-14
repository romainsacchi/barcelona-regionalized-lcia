# DAY 1 Notebooks

1. `D1-01 Python and Jupyter minimum refresher.ipynb`
2. `D1-02 Brightway architecture and data model.ipynb`
3. `D1-03 Manual LCA with NumPy matrices - Heijungs and Suh 2002 vs Brightway.ipynb`
4. `D1-04 First LCA from demand to score in Brightway.ipynb`
5. `D1-05 Uncertainty and Monte Carlo basics.ipynb`
6. `D1-06 Data quality checks and linking workflow.ipynb`
7. `D1-07 Contribution analysis and result visualization.ipynb`

Optional notebooks if time allows:

8. `D1-08 Optional - ecoinvent import and Brightway recap.ipynb`
9. `D1-09 Optional - Foreground and background uncertainty split.ipynb`
10. `D1-10 Optional - Database-level parameters and Monte Carlo.ipynb`

Assets for exercises are in `assets/`.

For `D1-04`, the bundled BAFU inventory Excel file is:
- `../../data/lci-bafu.xlsx`

During Day 1, participants import this bundled BAFU file into `brightway`.
The session also includes an `ecoinvent` import overview for participants who work with that database,
but `ecoinvent` is not included in this repository and is not used in the course exercises because of licensing constraints.
The optional `D1-08` notebook performs a real `ecoinvent 3.12 cutoff` import only for participants with valid `ecoinvent` credentials.
