# Notebook Refinement Questionnaire

Use this file to refine the course notebooks before expanding or revising them.
You can answer directly under each question or replace `TBD` with your response.

Suggested response styles:
- short bullet answers
- rough notes
- links to papers or repos
- explicit "keep as is" when no change is needed

## 1. Course-Level Decisions

### Audience and level

1. What is the actual learner profile you want to optimize for?
   Answer: they are LCA practitioners, but with very little Python and/or `brightway` experience. They know core LCA concepts but have not yet built their own models in Python.

2. How much Python fluency should we assume on Day 1 morning?
   Answer: beginner to intermediate. They can run code and understand basic syntax, but may not be comfortable with more complex data structures or libraries.

3. How much prior LCA modeling experience should we assume?
   Answer: 1-5 years of experience with LCA, but mostly in GUI tools or Excel. They understand the concepts of technosphere, biosphere, characterization factors, and uncertainty, but have not implemented these in code.

4. How much prior `brightway` experience should we assume?
   Answer: None. They may have heard of `brightway` but have not used it before. Day 1 will be their first hands-on experience with `brightway`.

5. Are you optimizing more for researchers, consultants, students, policy analysts, or a mixed audience?
   Answer: Priority to researchers and consultants who want to build their own models, but also open to students and policy analysts who want to understand the methods better.

6. What are the top 3 capabilities you most want participants to retain one month after the course?
   Answer: Handling databases in Brightway, modelling activities, running LCAs, and running regionlised LCIA with `edges`.

### Teaching format

7. What lecture-to-hands-on ratio do you want overall?
   Answer: More hands-on than lecture. Maybe 20% lecture, 80% hands-on notebooks.

8. Do you want notebooks to read like fully worked demos, partially guided labs, or mostly scaffolded exercises?
   Answer: mostly scaffolded exercises

9. Should each notebook be independently runnable, or is it acceptable that some depend on state created by earlier notebooks?
   Answer: it is acceptable that some depend on state created by earlier notebooks

10. Do you want hidden solution cells throughout, or only in selected exercise notebooks?
    Answer: I want hidden solution cells throughout

11. Should exercises be short "checkpoint" tasks every 10-20 minutes, or fewer larger exercises?
    Answer: short "checkpoint" tasks every 10-20 minutes

12. Do you want a consistent notebook template across all three days, or should Day 2 and Day 3 feel more advanced and less guided?
    Answer: a consistent notebook template across all three days

13. Should we optimize for live teaching by instructors, self-study after the course, or both equally?
    Answer: we optimize for live teaching by instructors

14. Should notebooks include more interpretation questions, more coding tasks, or more methodological critique?
    Answer: more coding tasks, but also some interpretation questions

15. Do you want explicit "common mistakes" or "debugging tips" callouts in notebooks?
    Answer: yes, especially in the setup and import notebooks

### Cross-cutting content choices

16. Which concepts must be repeated across multiple days because they are easy to forget?
    Answer: exchanges linking activities like edges link nodes, the difference between inventory and impact assessment, and the difference between variability and uncertainty.

17. Which topics are nice-to-have and could be cut if time runs short?
    Answer: `TBD`

18. Which topics should stay conceptual only, without hands-on implementation?
    Answer: `TBD`

19. Which topics should be demo-only by instructors rather than student exercises?
    Answer: `TBD`

20. Which outputs matter most: scalar scores, contribution plots, uncertainty distributions, maps, tables, or traceability outputs?
    Answer: scalar scores, contribution plots, uncertainty distributions, and traceability outputs. Maps and tables are nice but not essential for the core learning outcomes.

21. Should we include more visual outputs, and if yes which types?
    Answer: Yes, more visual outputs would be helpful. I would prioritize contribution plots (like bar charts or treemaps) and uncertainty distributions (like boxplots or histograms). Maps could be included for regionalised LCIA if time allows.

22. Are there any terms, modeling conventions, or notational choices you want standardized across all notebooks?
    Answer: we will use an attributional modelling approach (as opposed to consequential), and we will use the term "activity" for processes, "exchange" for flows between activities, and "characterization factor" for the impact per unit of flow.

23. Do you want every notebook to end with a short recap of "what you should now know"?
    Answer: Yes, I think a short recap at the end of each notebook would be helpful to reinforce the key takeaways. Also, a short list of bullet points at the beginning of each notebook summarizing the learning objectives would be good.

24. Should every notebook include references to one or more papers, or only selected notebooks?
    Answer: I think every notebook should include at least one reference to a relevant paper, but the depth of discussion can vary. Some notebooks might have a more detailed discussion of the paper, while others might just include a link for further reading.

25. Should paper references be background reading only, or directly tied to specific code cells and modeling choices?
    Answer: paper references should be background reading only

## 2. Dataset and Modeling Choices

26. For the bundled BAFU workbook, which sectors, activities, or flows should we highlight repeatedly in examples?
    Answer: powerplants, electricity production and passenger car transport are typically good examples for LCA teaching because they are familiar and have interesting regionalisation patterns. We can also include some agriculture or waste management examples if they are well represented in the BAFU dataset.

27. Which activities are the best pedagogical examples for a first LCA run from BAFU?
    Answer: those that relate to gasoline-fueled passenger car transport

28. Are there specific examples you want to avoid because they are confusing, too domain-specific, or too computationally heavy?
    Answer: no, but we hsould avoid empty or near-empty activities

29. Do you want one coherent case study threaded across all three days, or separate examples by topic?
    Answer: several separate examples by topic, but we can reuse some of the same activities or flows across notebooks to create some continuity.

30. If one cross-day case study is preferred, what should it be?
    Answer: the example of driving a battery-electric car could be good for this

31. How explicitly should we discuss the difference between BAFU and `ecoinvent` import workflows?
    Answer: very briefly. The BAFU LCA database is in fact a Swiss-centered variant of the ecoinvent database.

32. Should `ecoinvent` appear only in explanatory markdown, or should we include pseudocode / commented code showing the import pattern?
    Answer: we should include pseudocode / commented code showing the import pattern

33. Are there specific inventory flows, emissions, resources, or regions you want reused for regionalisation and scenario examples?
    Answer: The course happening in Barcelona, it would be good to include some examples from Spain or the Mediterranean region if they are well represented in the BAFU dataset. For example, we could look at electricity production in Spain, or passenger car transport in the region.

34. Should the examples stay Switzerland-centered because of BAFU, or broaden quickly to global/regional comparisons?
    Answer: if good datasets are only available for Switzerland, we can start with those, but I would like to broaden to global/regional comparisons as soon as possible, especially for the regionalised LCIA examples. We can use the BAFU dataset for the Swiss region and then show how to apply the same methods to other regions or global datasets.

## 3. Libraries, APIs, and Function Choices

35. Which `brightway` packages and APIs do you want used explicitly?
    Answer: brightway has sub-libraries such as bw2data (for handling projects and databases), bw2io (for importing and exporting data), bw2calc (ofr LCA calculation), bw2analyzer (for results interpretation), etc. We will use those depending on the notebook topic.

36. Which `brightway` objects/functions do you consider essential for participants to see directly in code?
    Answer: all relevant functions, that is to select a project, select a database, delete a project, rename a database, find an activity, run an LCA, run a MonteCarlo analysis, etc.

37. Which objects/functions should be hidden behind helper code because they are too distracting?
    Answer: `TBD`

38. Do you want notebooks to use `bw2data`, `bw2calc`, `bw2io`, and `bw2analyzer` directly by name in teaching text?
    Answer: yes

39. For Day 2, which `edges` functions, workflows, or abstractions must be demonstrated concretely?
    Answer: `TBD`

40. For Day 3, which libraries beyond `pandas` do you want used explicitly for scenario LCIA or inventory flow assessment?
    Answer: `TBD`

41. Do you want helper utilities created inside notebooks, or should code stay transparent even if repetitive?
    Answer: `TBD`

42. Should we use `matplotlib` only, or is there interest in richer plotting tools?
    Answer: `TBD`

43. Are there package-version constraints or API pitfalls we should design around in the teaching material?
    Answer: `TBD`

44. Do you want any lightweight helper module added to the repo later for repeated utility functions?
    Answer: `TBD`

## 4. Papers and References

45. Which paper is the anchor reference for Day 1?
    Answer: Mutel, (2017), Brightway: An open source framework for Life Cycle Assessment, Journal of Open Source Software, 2(12), 236, doi:10.21105/joss.00236 as well as Heijungs, R., Suh, S., 2002. The Computational Structure of Life Cycle Assessment. Kluwer Acad. Publ. https://doi.org/https://doi.org/10.1007/978-94-015-9900-9

46. Which paper is the anchor reference for Day 2?
    Answer: Sacchi, R., Menacho, A.H., Seitfudem, G. et al. Contextual LCIA without the overhead: an exchange-based framework for flexible impact assessment. Int J Life Cycle Assess 30, 3087–3101 (2025). https://doi.org/10.1007/s11367-025-02551-7 and Seitfudem, G., Berger, M., Schmied, H.M., Boulay, A.M., 2025. The updated and improved method for water scarcity impact assessment in LCA, AWARE2.0. J. Ind. Ecol. 29, 891–907. https://doi.org/10.1111/jiec.70023

47. Which paper is the anchor reference for Day 3 scenario LCIA?
    Answer: Barbosa Watanabe, M.D., Cherubini, F., 2026. Prospective Characterization Factors for Assessing Climate Change Impacts in Life Cycle Assessments. Environ. Sci. Technol. 60, 3202–3215. https://doi.org/10.1021/acs.est.5c12391 and Scherer, L., Rosa, F., Sun, Z., Michelsen, O., De Laurentiis, V., Marques, A., Pfister, S., Verones, F., Kuipers, K.J.J., 2023. Biodiversity Impact Assessment Considering Land Use Intensities and Fragmentation. Environ. Sci. Technol. 57, 19612–19623. https://doi.org/10.1021/acs.est.3c04191

48. Which paper is the anchor reference for Day 3 inventory flow / criticality?
    Answer: Koyamparambath, A., Loubet, P., Young, S.B., Sonnemann, G., 2024. Spatially and temporally differentiated characterization factors for supply risk of abiotic resources in life cycle assessment. Resour. Conserv. Recycl. 209, 107801. https://doi.org/10.1016/j.resconrec.2024.107801

49. Should the reading list be mapped notebook-by-notebook?
    Answer: Yes

50. Should each notebook reference one core paper only, or a small set of papers?
    Answer: A small set of papers, but with one anchor paper that is discussed in more depth.

51. For each of these candidate references, where should it appear and how heavily should it be used?
    - Sacchi et al. 2025 on contextual LCIA / exchange-based framework
    - Seitfudem et al. 2025 on AWARE2.0
    - Koyamparambath et al. 2024 on supply risk / differentiated CFs
    - Bulle et al. 2019 on IMPACT World+
    - Scherer et al. 2023 on biodiversity
    - Schipper et al. 2025 on IBIF
    - Watanabe and Cherubini 2026 on prospective CFs for climate change
   Answer: Sacchi et al. 2025 when we introduce `edges` and the exchange-based approach to LCIA, Seitfudem et al. 2025 when we discuss water scarcity impact assessment and how it can be regionalised, Koyamparambath et al. 2024 when we discuss inventory flow assessment and criticality, Bulle et al. 2019 as a background reference for regionalised LCIA methods, Scherer et al. 2023 when we discuss biodiversity impact assessment, Schipper et al. 2025 when we discuss country-level biodiversity intactness footprints, and Watanabe and Cherubini 2026 when we discuss scenario-based LCIA with prospective characterization factors.

52. Are there missing references not yet listed in `READING_MATERIAL.md` that should drive notebook content?
    Answer: `TBD`

53. Do you want references cited in APA form inside notebooks, or just a short author-year mention with link?
    Answer: references should be cited in APA form inside notebooks

## 5. Setup Notebook

Relevant file: `tutorials/00_SETUP/00 - Setup and First Checks.ipynb`

54. Should the setup notebook stay minimal, or should it include a stronger environment-diagnosis workflow?
   Answer: it should include a stronger environment-diagnosis workflow

55. Should it verify package imports beyond core `brightway`, for example `edges`?
   Answer: Yes

56. Should it include a short explanation of how file paths differ on Mac vs Windows?
   Answer: No

57. Should it explicitly check that `data/lci-bafu.xlsx` exists and maybe print file size / modified date?
   Answer: Not necessarily, but it could be helpful to confirm that the file is present and has the expected size. We could add a cell that checks for the file and prints a warning if it's missing or has an unexpected size.

58. Should it include a tiny "open notebook, run cells, switch kernel" micro-tutorial for beginners?
   Answer: Yes

59. Which setup failures are most common and worth anticipating explicitly?
   Answer: Missing dependencies, missing solver for bw2calc (PYPARDISO, or UMFPACK for Macs), and issues with the Python environment (e.g., not activating the `bw2` environment). We could include troubleshooting tips for these common issues. also, if the solver is absent, a message will display upon import of bw2data.

## 6. Day 1 Overall

Day 1 notebooks:
- `D1-01 Python and Jupyter minimum refresher`
- `D1-02 Brightway architecture and data model`
- `D1-03 Manual LCA with NumPy matrices`
- `D1-04 First LCA from demand to score in Brightway`
- `D1-05 Uncertainty and Monte Carlo basics`
- `D1-06 Data quality checks and linking workflow`
- `D1-07 Contribution analysis and result visualization`

60. What is the core narrative arc for Day 1?
    Answer: Day 1 is about building a strong foundation in `brightway` and LCA modeling. We start with a Python refresher to ensure everyone is comfortable with the tools, then we dive into the architecture and data model of `brightway` to understand how it works under the hood. Next, we do a manual LCA with NumPy matrices to connect the mathematical concepts of LCA with the computational implementation. After that, we run our first LCA in `brightway` using the BAFU dataset (where we also see how to import databases), which gives us a practical example of how to set up and run an LCA. Finally, we cover uncertainty and Monte Carlo basics to introduce participants to more advanced analysis techniques.

61. Which Day 1 topics are mandatory before participants can succeed on Day 2?
    Answer: activate projects, select databases, find activities, run an LCA, and understand the difference between activities and exchanges. Also, understanding the data model of `brightway` is important for Day 2 when we start working with `edges` and regionalised LCIA.

62. How deep should Day 1 go into Brightway internals versus practical usage?
    Answer: it should prioritize practical usage, but with enough explanation of internals to build confidence and understanding. We want participants to be able to use `brightway` effectively, but also to understand how it works so they can troubleshoot and customize their models in the future.

63. Should Day 1 be more "learn the architecture" or more "build confidence by doing"?
    Answer: "build confidence by doing"

64. What is the single most important conceptual bridge between D1-03 and D1-04?
    Answer: in D1-03, we will do a manual LCA using NumPy matrices, using the approach of Heijungs and Suh 2002 and that of Brightway, to understand teh difference. In D1-04, we will run a first LCA in Brightway using the BAFU dataset. The conceptual bridge is understanding how the manual matrix approach relates to the way `brightway` structures data and runs calculations. We want participants to see that the technosphere and biosphere matrices they constructed manually are essentially what `brightway` is doing under the hood when it runs an LCA.

65. Where exactly should the `ecoinvent` overview fit on Day 1?
    Answer: When we import the BAFU database, we want to see how one would import the ecoinvent database, if one had such a database.

66. Should the `ecoinvent` overview be a short markdown digression in `D1-04`, a dedicated section, or a separate notebook later?
    Answer: a dedicated section

## 7. D1-01 Python and Jupyter Minimum Refresher

67. What is the real goal of `D1-01`: absolute beginner onboarding, confidence warm-up, or filtering out setup issues?
    Answer: confidence warm-up and filtering out setup issues

68. Which Python concepts are essential here: variables, lists, loops, functions, dictionaries, imports, pandas basics, file paths?
    Answer: variables, lists, loops, functions and dictionaries

69. Which concepts should be omitted to keep this notebook short?
    Answer: classes, decorators, context managers, file paths (maybe), and advanced pandas features

70. Should this notebook use LCA-flavored examples immediately, or generic Python examples?
    Answer: this notebook can use LCA-flavored examples

71. What is the ideal duration for this notebook in live teaching?
    Answer: 30 minutes

72. Should there be one or two micro-exercises here, and what should they test?
    Answer: no. We expect the students to have gone through Python tutorials prior to the course, so this notebook is more of a refresher and confidence builder rather than a full tutorial. We can include some small "try it yourself" cells where they can modify code or run simple commands, but we don't need formal exercises here.

## 8. D1-02 Brightway Architecture and Data Model

73. Which Brightway architecture concepts must be visible in code, not just described?
    Answer: projects, databases, activities, exchanges, and methods should all be visible in code. We want participants to see how these concepts are represented in `brightway` and how they interact with each other.

74. Should this notebook explicitly explain projects, databases, methods, activities, exchanges, and matrices one by one?
    Answer: yes, and how they relate to each other. For example, we can show how a project contains databases, how databases contain activities, how activities have exchanges, and how methods are used to calculate impacts based on those exchanges.

75. How much should it relate the data model to what participants will import from BAFU later that day?
    Answer: not at this stage. We can use simple toy examples to illustrate the data model, and then later when we import the BAFU dataset, we can show how the same concepts apply to the real data. This way, participants can first understand the architecture in a simplified context before seeing it in action with the BAFU dataset.

76. Which `bw2data` inspection patterns do you want students to practice?
    Answer: create, activate projects, delete projects, create databases, find activities, inspect exchanges, and understand how to navigate the data structure. We can also show how to use the `bw2data` API to query for specific information about activities and exchanges. But we will actually do this in the context of the BAFU dataset in D1-04, so we can keep it more conceptual here.

77. Should this notebook include a small "find one activity / inspect one exchange" exercise?
    Answer: maybe we will do that once we have imported the BAFU database in D1-04, but we can also include a small exercise here with a toy database that we create just for this notebook. This way, participants can practice the inspection patterns in a simple context before applying them to the real dataset.

78. Which paper or documentation source should anchor this notebook?
    Answer: Mutel (2017) for the overall architecture.

## 9. D1-03 Manual LCA with NumPy Matrices

79. How rigorous should the Heijungs and Suh style derivation be?
    Answer: as rigorous as can be, reusing the same letters, and vector and matrices shaped. this is detailed in teh publication. We do not have to use the same example as in the publication though.

80. What do you want participants to understand from the manual matrix notebook that they would otherwise miss?
    Answer: the idea is to understand the mathematical structure of LCA and how it relates to the way `brightway` organizes data and runs calculations. By doing a manual LCA with NumPy matrices, participants can see how the technosphere and biosphere matrices are constructed, how the demand vector is defined, and how the characterization factors are applied to calculate impacts. This will help them understand what `brightway` is doing under the hood when it runs an LCA, and give them more confidence in using `brightway` effectively. The objective is also to understand tha tthe brightway approach differs slightly from Heijungs and Suh, as Brightway preserve items in their matrix form.

81. Should the notebook derive the technosphere solve, biosphere inventory, and characterization step explicitly?
    Answer: yes, we can use a simple CAM example inspired by the supplementary numerical illustration prepared for the exchange-based LCIA paper response.

82. Do you want one tiny toy system only, or multiple small systems?
    Answer: we cna work with 2 or 3 examples, but they should be small and simple enough to run quickly and be easily understood. We can start with a very simple system with just a few activities and exchanges, and then maybe add one or two more examples that are slightly more complex but still manageable.

83. Should the toy system resemble the later BAFU import example, or stay fully abstract?
    Answer: they should stay fully abstract, to focus on the mathematical structure rather than the specific domain. We can use generic names for activities and flows, like "Activity A", "Activity B", "Flow X", etc., to keep it simple and clear.

84. Which `numpy` operations should be shown directly?
    Answer: the LCA computaiton structure require matrix multiplication, matrix inversion, and element-wise multiplication. We can show how to construct the technosphere and biosphere matrices as NumPy arrays, how to define the demand vector, and how to apply the characterization factors. We can also show how to solve the system of equations to get the activity levels and then calculate the impacts.

85. Where should the exercise sit: after matrix construction, after solving, or after comparison with Brightway?
    Answer: the ideal exercise would be to have participants construct the matrices and demand vector for a simple system, then solve it manually, and finally compare their results with what `brightway` gives for the same system. This way, they can see the full workflow from manual calculation to software implementation.

86. How much time do you want to spend on comparing manual results to Brightway results?
    Answer: we will not use directly Brightway here, but we will manually recreate the workflow Bright way uses.

## 10. D1-04 First LCA from Demand to Score in Brightway

87. What should this notebook emphasize most: project setup, import mechanics, database inspection, or first score calculation?
    Answer: project setup, import mechanics (we will import the BAFU database here), database inspection (we will inspect the imported database and find some activities and exchanges), and first score calculation (we will run a first LCA using the imported database). All of these are important, but I would say the import mechanics and first score calculation are the most critical for this notebook.

88. Should the BAFU import workflow be treated as the main practical milestone of Day 1?
    Answer: yes, the BAFU import workflow is a key practical milestone for Day 1. It will give participants hands-on experience with importing a real LCA database into `brightway`, which is a crucial skill for building their own models in the future. We can also use this opportunity to discuss best practices for data hygiene and preparation before import. That database will be used i DAY 2 and 3 as well.

89. Which import steps do students need to understand deeply: `ExcelImporter`, strategies, biosphere matching, statistics, database writing?
    Answer: `ExcelImporter`, strategies, biosphere matching, statistics, unlinked exchanges, database writing.

90. Which import steps can be treated as "standard pipeline" without too much detail?
    Answer: `TBD`

91. Do you want the notebook to explain how a similar workflow would work for `ecoinvent`?
    Answer: Yes, we should have a section showing how to import ecoinvent, as it is a popular database. However, the ecoinvent import has its own import conveniency functions. We can show the general pattern of how to use `bw2io` for importing, and then show the specific functions for ecoinvent import. This way, participants can understand the general principles of importing databases with `bw2io`, and also see how it applies to a specific case like ecoinvent.

92. If yes, should that explanation mention specific `bw2io` importers or stay conceptual?
    Answer: that explanation mention specific `bw2io` importers. We will just not run it, but we will show the code and explain how it works.

93. Should students inspect the imported database immediately after import?
    Answer: Yes, we can review here the concepts of database, activities, exchanges, etc.

94. Which specific BAFU activity should be used if you do not want a random activity for the first LCA?
    Answer: We can use a coal-fired power plant.

95. Should this notebook include a troubleshooting section for failed imports or poor matching?
    Answer: We will see that in D1-06, but we can include a brief troubleshooting section here as well, especially if we encounter any issues during the import process. We can also include some tips for how to check the imported data and identify any potential issues.

96. What is the best small exercise for this notebook besides "import under a second name"?
    Answer: We will do that in D1-06.

## 11. D1-05 Uncertainty and Monte Carlo Basics

97. What is the target depth here: conceptual introduction or actual practitioner-ready Monte Carlo workflow?
    Answer: actual practitioner-ready Monte Carlo workflow. we assume the students know already about uncertainty in LCA.

98. Which uncertainty concepts matter most: distributions, sampling, propagation, interpretation, convergence?
    Answer: distribution definitions (brightway uses the stats_array library) in life cycle inventory exchanges, and how that propagates in the scores and contribution analysis. We can also touch on interpretation and convergence, but the main focus should be on how to set up and run a Monte Carlo analysis in `brightway`. We can inspire ourselves from: /Users/romain/GitHub/winter-school-psi-2025/tutorials/brightway/1 - BW structure and first LCAs.ipynb

99. Should the notebook use toy uncertainty examples first, or jump directly into Brightway Monte Carlo?
    Answer: the BAFU database has uncertainty distribution definitions in its exchanges, so we can use those directly to show how to run a Monte Carlo analysis in `brightway`. We can also include a brief conceptual introduction to uncertainty and Monte Carlo methods at the beginning of the notebook, but we can jump directly into the practical application with the BAFU dataset.

100. Which Brightway Monte Carlo APIs do you want highlighted?
     Answer: the bw2calc.LCA class has an argument use_distribution=True that allows you to run a Monte Carlo analysis. We can also show how to access the results of the Monte Carlo analysis, such as the distribution of scores and the contribution analysis for each iteration.

101. Should this notebook produce histograms, confidence intervals, percentiles, or convergence plots?
     Answer: yes, we can produce histograms of the score distribution, calculate confidence intervals, and show percentiles. We can also include a brief discussion of how to interpret these results and what they mean for decision-making.

102. What is the key interpretation lesson students should retain?
     Answer: if the confidence intervals of two product system significantly overlap, it is difficult to rank them, and maybe statistical test are needed to show the significance of the difference. Also, contribution analysis can show which activities or exchanges are driving the uncertainty in the scores.

103. Where should the exercise go, and what should students compute or interpret?
     Answer: the exercise could be to run a Monte Carlo analysis on a couple of specific activity (e.g., the coal-fired power plant vs a natural gas power plant) and then interpret the respective results, their overlap in score distribution and  contribution analysis. We can ask students to identify which activities or exchanges are contributing most to the uncertainty in the score, and to discuss what that means for improving the model or making decisions.

## 12. D1-06 Data Quality Checks and Linking Workflow

104. Should this notebook stay on CSV-style foreground checks, or move closer to realistic Brightway import-prep workflows?
     Answer: this notebook should primarily be about importing foreground inventoriy files (which I'll provide), that contains error, which prevent their liking to the background database BAFU. We will then see how to debug that, identify problematic exchanges, apply migration files and solve the import. We should inspire ourselves from : /Users/romain/GitHub/winter-school-psi-2025/tutorials/brightway/2 - Data IO & contribution analyses.ipynb

105. Which data quality failure modes matter most to teach here?
     Answer: unlinked exchanges (biosphere, technosphere, wrongly spelled exchanges, etc.), and how ot apply migrations to solve those issues.

106. Do you want to cover missing technosphere links only, or also units, categories, duplicate codes, naming mismatches, biosphere mapping issues?
     Answer: missing technosphere links, units, categories, duplicate codes, naming mismatches, biosphere mapping issues

107. Should the exercise dataset become more realistic and domain-specific?
     Answer: realistic yes, as I'll provide proper foreground inventories, but domain-specific, not really.

108. Would it help to connect this notebook more explicitly to Excel import hygiene?
     Answer: yes

109. Which `pandas` operations do you want students to practice here?
     Answer: I don't think we shold focus on `pandas` here.

110. Should this notebook end with a "checklist before import" summary?
     Answer: not really.

## 13. D1-07 Contribution Analysis and Result Visualization

111. Which contribution analysis views matter most: top activities, top emissions, processes by stage, Sankey-like structure?
     Answer: top activities, top emissions and Sankey-like structure

112. Should contribution analysis use the BAFU import result directly?
     Answer: we cna either use a random activity from BAFU or we can use the same activity as in D1-05, to show how uncertainty and contribution analysis can be combined.

113. Which visualization style do you prefer for the course: plain bar charts, stacked bars, treemaps, waterfall charts, or something else?
     Answer: stacked bars. We cna also use `polyviz`, a library I amde for visualizing Brightway results. We can inspire ourselfves from this notebook: /Users/romain/GitHub/winter-school-psi-2025/tutorials/brightway/2 - Data IO & contribution analyses.ipynb

114. Do you want students to learn interpretation pitfalls, such as confusing contribution with sensitivity or causality?
     Answer: No, out of scope for this course.

115. What should the exercise ask them to conclude from the plotted results?
     Answer: how much of impacts happen in the foreground vs background, how do they distirbute regionally (to make a good transition to Day 2), and which emissions or activities are the main contributors to the score.

## 14. Day 2 Overall

Day 2 notebooks:
- `D2-01 Day 1 recap and readiness checks`
- `D2-02 Edges fundamentals and regionalisation concepts`
- `D2-03 Spatial matching and fallback logic`
- `D2-04 Regionalised methods across impact categories`
- `D2-05 Variability and uncertainty in regionalised LCIA`
- `D2-06 Case study - Regionalised electricity mix`

116. What is the main narrative arc for Day 2?
     Answer: During Day 2, we want to understand the matrix formulation of `edges`, whihc differs slightly from teh conventional one, and allows for injecting specific characterization factors (off-diagonal) into the characterization matrix, to allow for echange-based LCIA. We will also see how `edges` implements a spatial matching and fallback logic to assign regionalized CFs to exchanges based on their geographies. Then we will explore how regionalised methods differ across impact categories, and how to interpret variability and uncertainty in regionalised LCIA results. Finally, we will apply these concepts in a case study comparing regionalised electricity mixes.

117. Which Day 1 assumptions need to be explicitly revisited before regionalisation starts?
     Answer: we assume teh participants have understood teh matrix formulation of LCA, but we will see that `edges` uses a slightly different formulation that allows for exchange-based LCIA. We also assume that participants understand how to run a basic LCA in `brightway`, but we will see how to extend that workflow to include regionalised characterization factors and spatial matching. But it is important to understand the difference.

118. Should Day 2 feel method-heavy, software-heavy, or decision-use heavy?
     Answer: it should rather feel method-heavy: first, because we unveil the `edges` method and new matrix formulation, second, because we unveil the mapping logic of `edges` and third because we also look at the method of a couple of regionalized impact assessment methods like AWARE 2.0.

119. What should participants be able to do by end of Day 2 that they could not do after a standard Brightway introduction?
     Answer: They should understand the matrix formulation of `edges`, they should be able to run `edges` for regionalised LCIA, they should understand the spatial matching and fallback logic of `edges`, and they should be able to interpret variability and uncertainty in regionalised LCIA results.

120. Which regionalised impact categories should receive the most emphasis?
     Answer: We will look at water scarcity (AWARE 2.0) and biodiversity (IBIF). We leave scenario-based and material criticality CFs for Day 3.

121. Which categories are too complex or too distracting for this audience?
     Answer: `TBD`

## 15. D2-01 Day 1 Recap and Readiness Checks

122. Should this notebook be a true recap with conceptual questions, or mostly an environment/package sanity check?
     Answer: It should be a recap of the key concepts (projects, database, activities, exchanges, methods), a recap of the matrix formulation, and the general workflow to run simple LCAs. And also a sanity check to ensure that the environment is set up correctly and that the BAFU database is imported and ready to use.

123. Which imports, versions, and data objects should it validate before Day 2 starts?
     Answer: It should validate the import of brightway modules, the presence of the BAFU database, and `edges`.

124. Should it include a short quiz or recall exercise from Day 1?
     Answer: Yes, we can include a short quiz with multiple choice questions or short answer questions to test participants' recall of key concepts from Day 1. This can help reinforce their understanding and identify any areas that may need further clarification before we dive into the more advanced topics of Day 2.

125. What would be the best readiness signal before moving into `edges`?
     Answer: `TBD`

## 16. D2-02 Edges Fundamentals and Regionalisation Concepts

126. What does this notebook need to accomplish beyond "Edges extends Brightway"?
     Answer: We do not want to start using `edges` right away. We want to redo a manual LCA like we did in DAY 1, with teh CAM example and water flows. And then, we do a second pass where we apply the `edges` approach (without using `edges`) where we multiply the inventory matrix with a hand-made characterization matrix in which we inject location-specific factors. This way, we can show the difference between the conventional LCA approach and the `edges` approach, and how the latter allows for more flexibility in applying regionalised characterization factors.

127. Which `edges` abstractions or data structures should students understand by name?
     Answer: "exchange-based" characterization factors, the `edges` matrix formulation, and "edge-attributes", meaning the attributes of the nodes on both end of the edges (which are the supplier or the consumer). Attributes can be a name, a product, and also, importantly, a location/geography.

128. Should this notebook compare global CFs and regionalised CFs with one concrete mini-example?
     Answer: Yes, we can use teh CAM exmaple of DAY 1, and we cna use teh conventional matrix formulation where we use a global characterization factor of 39.5 in teh characterization matrix. We can then use the `edges` approach where we inject location-specific AWARE factors for the exchanges, so the same biosphere flow can receive different characterization factors depending on where the withdrawal happens.

129. Which reference paper should anchor the conceptual framing here?
     Answer: Sacchi et al. 2025 on contextual LCIA / exchange-based framework

130. Which `edges` functions or package entry points should appear in code?
     Answer: we will not use `edges` directly in this notebook, but we will show how to set up the matrices in a way that is compatible with the `edges` approach. We can also show some of the key functions in `edges` that are used for applying regionalised characterization factors and running the calculations, but we will save the actual use of `edges` for the next notebook. 

131. What is the best short exercise here?
     Answer: the exercise could be to take a simple LCA example (like the CAM example from Day 1) and apply the `edges` approach manually by constructing a characterization matrix that includes both global and regionalised factors, and then calculating the impacts. This will help participants understand how the `edges` approach differs from the conventional approach and how it allows for more flexibility in applying regionalised characterization factors.

## 18. D2-03 Introduction to `edges` workflow and API

132. Should this notebook be a full `edges` tutorial, or just a quick demo of the main workflow?
     Answer: it should be a quick demo of the main workflow, showing how to set up and run `edges` for regionalised LCIA and to understand how to formulate and build method JSON files.
     We must integrate the notebook examples "lcia_example_1.json" to "lcia_example_6.json" bundled under `tutorials/DAY 2/assets/edges_examples/`.
     We can show how to prepare the data, how to define the regionalised characterization factors, and how to run the calculations. We can also show how to interpret the results and compare them with a conventional LCA approach. 

133. Which `edges` functions or classes should be highlighted in code?
     Answer: we can highlight the main functions for setting up the matrices, defining the regionalised characterization factors, and running the calculations. We can also show how to use the `edges` API to access the results (the pandas dataframe listing exchanges) and perform analysis.


## 19. D2-04 Spatial Matching and Fallback Logic

134. How deep should this notebook go into matching logic internals?
     Answer: it should go deep enough to explain the main matching rules and how they are applied in `edges`, but it does not need to cover every single detail of the implementation. The focus should be on understanding the key concepts of spatial matching, such as exact match, country-to-region mapping, region-to-world mapping, and fallback chains, and how these are used to assign regionalised characterization factors to exchanges based on their geographies. We can also include some examples to illustrate how the matching logic works in practice.

135. Which matching rules matter most to explain: exact match, country-to-region, region-to-world, fallback chains?
     Answer: `edges` has four mapping strategies: direct mapping, mapping aggregated regions (e.g., Europe, which is made fo several countries), mapping to dynamic locations (e.g., RoW, whihc is made of countries which are not covered by other datasets for that given activity), mapping of contained locations (e.g., "CA-QC" Québec, whihc, if no factors can be found, can be given teh factor of Canada that contains it). Finally, if some edges are eligible for receiving a factor but did not, a global factor is given.

136. Should the notebook include a table-driven exercise where students predict matches before running code?
     Answer: Yes, we can include a table with different geographies for the supplier and consumer of an exchange, and ask students to predict which matching rule would apply and what kind of characterization factor they would receive. Then we can run the code to see the actual matches and compare with their predictions. This will help them understand the matching logic and how it applies to different scenarios.

137. Which geographies should be used as examples?
     Answer: we can use a variety of geographies, such as specific countries (e.g., France, Germany), regions (e.g., Europe, North America), and dynamic locations (e.g., RoW). We can also include examples of contained locations (e.g., a specific state or province within a country) to illustrate the different matching rules.

138. Should ambiguity and epistemic uncertainty in spatial matching be emphasized?
     Answer: No, we will focus on the mechanics of the matching logic rather than the uncertainty or ambiguity that may arise from it.

## 20. D2-05 Regionalised Methods Across Impact Categories

139. Which impact categories should definitely be demonstrated here?
     Answer: we should definitely demonstrate water scarcity (using AWARE 2.0) and biodiversity (using the Laura Scherrer biodiversity method). These are two impact categories where regionalisation is particularly important and where there are well-established methods for applying regionalised characterization factors.

140. Do you want category-by-category interpretation, or a compact comparative overview?
     Answer: A category-by-category interpretation would be more effective for teaching purposes, as it allows us to dive into the specifics of each impact category and how regionalisation affects the results. We can then provide a compact comparative overview at the end to summarize the key differences and similarities across categories. We could look at teh papers describing AWARE 2.0 and the Laura Scherrer biodiversity method, and we can also look at the paper by Romain Sacchi on exchange-based LCIA, which includes examples of regionalised characterization factors for different impact categories.

141. Which paper or method documents should be cited for each category?
     Answer: - For water scarcity, we should cite the AWARE 2.0 method paper by Seitfudem et al (2025) and for the biodiversity paper, it should be from Scherrer et al. (2024)..

142. Should students compare rankings across categories and discuss why they differ by region?
     Answer: Yes, we can include an exercise where students compare the rankings of different product systems across the water scarcity and biodiversity impact categories, and discuss how and why the rankings differ based on the regionalised characterization factors. This will help them understand the importance of regionalisation and how it can affect decision-making in LCA.

143. What small exercise belongs here?
     Answer: the exercise could be to take a specific activity from the BAFU database (e.g., a water withdrawal in a specific location) and calculate its impact on both water scarcity and biodiversity using the regionalised characterization factors from AWARE 2.0 and the Laura Scherrer method. Then, students can compare the results and discuss how the regionalisation affects the impacts in each category.

## 21. D2-06 Variability and Uncertainty in Regionalised LCIA

144. How should this differ from the Day 1 uncertainty notebook?
     Answer: Here, we're not considering teh uncertainty at the inventory level, unlike DAY 1, but rather the variability and uncertainty that arises from the regionalisation of characterization factors. This includes understanding how different matching rules can lead to different characterization factors being applied to the same exchange, and how this can affect the overall results and rankings of product systems. We can also discuss the implications of this variability for decision-making and how to communicate it effectively.

145. Are you focusing more on spatial variability, parameter uncertainty, scenario uncertainty, or all three?
     Answer: spatial variability. For exmaple, in the AWARE implementation, we have multiple factors for a same region, depending on which watershed teh water is withdrawn from. So, we can have a same activity with the same geography, but which receives different characterization factors depending on the specific location of the exchange. This is a form of spatial variability that arises from the regionalisation process.

146. Should uncertainty here be mostly interpretive, or computational with repeated runs / distributions?
     Answer: computational with repeated runs / distributions. `edges` allows for running Monte Carlo analyses that take into account the variability in characterization factors due to regionalisation, so we can show how to set up and run such analyses, and how to interpret the results. It allows also for a multitude of distributions.

147. Which outputs best communicate the message: boxplots, maps, ranges, rank instability?
     Answer: probably boxplots

148. What is the key cautionary lesson for practitioners?
     Answer: the key cautionary lesson is that regionalisation can introduce significant variability in the results of an LCA, and this variability can affect the rankings of product systems. Therefore, it is important for practitioners to be aware of this variability and to communicate it effectively when presenting LCA results. It also highlights the importance of using regionalised characterization factors when they are available, as they can provide a more accurate representation of the environmental impacts in different regions.

## 22. D2-07 Case Study - Comparison of electrolytic hydrogen production pathways across regions

149. Is this the main Day 2 integrative exercise?
     Answer: Yes. We want to compare three ways of producing electrolytic hydrogen: a PEM electrolyser, a solid oxide electrolyser, and a conventional alkaline electrolyser. We want to compare these three technologies across different regions or electricity mixes, to see how the regionalisation of characterization factors affects the results and rankings of these technologies with respect to water scarcity and biodiversity impacts.

148. Which regions or electricity mixes should be compared?
     Answer: We could pick different SPain regions and different France regions. We will need to fetch high-resolution characterization factors for Spain and France from the WULCA website. We will also need to create a separate foreground atabase, where we duplicate the same electrolyser activity for each region, and link it to the corresponding regionalised characterization factors. This way, we can run the LCA for each region and compare the results.

149. Should the case study use the existing `scenario_table_electricity.xlsx`, or should that asset be reworked?
     Answer: No, we will use the regular average low-voltage electricity datasets from BAFU for Spain and France.

150. What is the core decision question participants should answer?
     Answer: The core decision question is: how does the choice of region (and therefore the regionalised characterization factors) affect the environmental impacts and rankings of different electrolytic hydrogen production technologies with respect to water scarcity and biodiversity? This will help participants understand the importance of regionalisation in LCA and how it can influence decision-making. Hopefully, we might uncover a trade-off between water scarcity and biodiversity impacts.

151. Which indicators should be mandatory in the case study?
     Answer: we should at least include water scarcity (using AWARE 2.0) and biodiversity (using the Laura Scherrer method). We can also include a global warming potential indicator for comparison, but the main focus should be on the regionalised impact categories.

152. Should teams present results briefly at the end of Day 2?
     Answer: This is a good idea, as it allows participants to share their findings and interpretations with each other, and to discuss the implications of the results. We can allocate a short time slot at the end of Day 2 for each team to present their results and key takeaways.

153. What is the ideal final deliverable from this notebook?
     Answer: The ideal final deliverable would be a set of results comparing the impacts of the different electrolytic hydrogen production technologies across the different regions, with a clear interpretation of how regionalisation affects the results and rankings. This could be in the form of a notebook with tables and plots, and a brief written summary of the key findings and implications for decision-making.

## 21. Day 3 Overall

Day 3 notebooks:
- `D3-01 Day 2 recap and scenario framing`
- `D3-02 Parameterised CFs for scenario-based LCIA`
- `D3-03 Time and scenario integration workflow`
- `D3-04 Inventory flow assessment I - tracing intermediates`
- `D3-05 Inventory flow assessment II - criticality factors`
- `D3-06 Capstone dual case study`

154. What is the main narrative arc for Day 3?
     Answer: `TBD`

155. How do you want to balance scenario LCIA versus inventory flow assessment?
     Answer: `TBD`

156. Which of the two Day 3 themes is strategically more important for this audience?
     Answer: `TBD`

157. Should Day 3 feel exploratory and frontier-like, or still methodically grounded and conservative?
     Answer: `TBD`

158. Which papers should participants remember from Day 3?
     Answer: `TBD`

## 22. D3-01 Day 2 Recap and Scenario Framing

159. What exactly should be recapped from Day 2 before introducing scenarios?
     Answer: `TBD`

160. What does "scenario framing" mean in your intended teaching design?
     Answer: `TBD`

161. Should this notebook include a conceptual distinction among scenario, uncertainty, and sensitivity analysis?
     Answer: `TBD`

162. What is the best exercise here?
     Answer: `TBD`

## 23. D3-02 Parameterised CFs for Scenario-Based LCIA

163. How realistic should the parameterised CF example be?
     Answer: `TBD`

164. Should parameterisation be shown with simple tables only, or tied to actual method structures?
     Answer: `TBD`

165. Which environmental mechanism should anchor the scenario example?
     Answer: `TBD`

166. Which paper should be cited most directly here?
     Answer: `TBD`

167. Which code pattern do you want: simple `pandas` transformation, function-based scenario generation, or something more formal?
     Answer: `TBD`

168. What should students produce in the exercise?
     Answer: `TBD`

## 24. D3-03 Time and Scenario Integration Workflow

169. What is the conceptual goal of integrating time and scenarios in this notebook?
     Answer: `TBD`

170. How deep should temporal differentiation go?
     Answer: `TBD`

171. Should the notebook include actual temporal indexing logic or remain at a tabular workflow level?
     Answer: `TBD`

172. Which example timeline or scenario families should be used?
     Answer: `TBD`

173. What is the most important practitioner takeaway?
     Answer: `TBD`

## 25. D3-04 Inventory Flow Assessment I - Tracing Intermediates

174. What do you want participants to mean by "inventory flow assessment" after this notebook?
     Answer: `TBD`

175. Which materials or intermediates should be traced?
     Answer: `TBD`

176. Should this notebook emphasize tracing logic, supply-chain interpretation, or algorithmic structure?
     Answer: `TBD`

177. Which examples will make the motivation obvious?
     Answer: `TBD`

178. Should the notebook remain conceptual with tables, or include graph traversal / recursive logic?
     Answer: `TBD`

179. Which paper should anchor this notebook?
     Answer: `TBD`

## 26. D3-05 Inventory Flow Assessment II - Criticality Factors

180. How should this notebook build directly on D3-04?
     Answer: `TBD`

181. Which criticality dimensions matter most: supply risk, concentration, geopolitical vulnerability, temporal dynamics?
     Answer: `TBD`

182. Which differentiated CF dataset or paper should be highlighted?
     Answer: `TBD`

183. Should the notebook include a formula-level explanation of criticality factors?
     Answer: `TBD`

184. What should students actually calculate here?
     Answer: `TBD`

185. What interpretation caveats should be made explicit?
     Answer: `TBD`

## 27. D3-06 Capstone Dual Case Study

186. Should this capstone integrate both scenario LCIA and inventory flow in one coherent story, or keep them as parallel tasks?
     Answer: `TBD`

187. What is the ideal capstone topic?
     Answer: `TBD`

188. Should teams choose between cases, or should everyone work on the same case?
     Answer: `TBD`

189. What output format do you want: notebook completion, short oral report, slide, markdown summary, or all of these?
     Answer: `TBD`

190. How much instructor scaffolding should remain in the capstone notebook?
     Answer: `TBD`

191. What would count as a strong capstone outcome by 19:00 on Day 3?
     Answer: `TBD`

## 28. Exercise Design

192. Across the course, how many exercises should be individual vs pair/group work?
     Answer: `TBD`

193. What is the typical target duration of a "small exercise"?
     Answer: `TBD`

194. Do you want exercises to emphasize coding, interpretation, or methodological critique?
     Answer: `TBD`

195. Should each notebook contain exactly one exercise section, or multiple small checkpoints?
     Answer: `TBD`

196. Should answers be automatically checkable anywhere, or is open-ended interpretation enough?
     Answer: `TBD`

197. Which notebooks most need stronger exercises than they currently have?
     Answer: `TBD`

198. Which notebooks currently have too much exercise scaffolding and should become more concise?
     Answer: `TBD`

## 29. Deliverables for the Next Revision Pass

199. If I revise the notebooks next, should I aim for:
     - stronger markdown explanations
     - more realistic code
     - better examples
     - more exercises
     - better references
     - more consistent style
     - all of the above, prioritized
   Answer: `TBD`

200. Which 3 notebooks should be improved first?
     Answer: `TBD`

201. Which notebook should remain intentionally lightweight?
     Answer: `TBD`

202. Do you want me to propose a revised notebook-by-notebook teaching plan after you answer this file?
     Answer: yes

203. Do you want me to directly rewrite notebooks after your answers, or first produce a design memo?
     Answer: first produce a design memo
