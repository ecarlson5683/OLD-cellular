# OLD-cellular
Data analysis for aging-ethanol collaboration by Erika R. Carlson, Laura K. Fonken, and Kimberly Nixon

## Overview 
This repository contains data and code used for the analyses presented in the manuscript titled "XXX" (Carlson, Fonken, and Nixon, in preparation).

The RMarkdown document titled "OLD_Analyses.Rmd" includes R code to:
- Read cell count data
  - Iba1+ for microglia
  - MHCII+ for antigen-presenting cells
  - CD68+ for phagocytic/lysosomal-enriched cells
- Calculate % co-labeling
  - MHCII+/Iba1+ of total Iba1+ for antigen-presenting microglia
  - CD68+/Iba1+ of total Iba1+ for phagocytosing microglia
- Calculate morphology
- Read densitometry data
  - Vimentin % area for reactive astrocytes
- Conduct two-way ANOVA on cell count data with age (aged (~25 mo) vs adult (~4 mo)) and diet (ethanol vs control) as between-subjects factors along with pairwise comparisons of simple effects with Bonferroni correction when appropriate.
- Read data related to intoxication behavior, ethanol dose, and blood ethanol concentrations and conduct Welch t-tests.

## Dependencies
The following packages are required to run this code and can be installed using `install.packages("<package>")`:
- {tidyverse}
- {afex}
- {emmeans}
- {rstatix}

## ***data*** Directory
The ***data*** directory includes the following files:
- **intoxication.csv**: Contains behavioral intoxication scores for each dosing session (every 8 h) with the following variables (n = XX, XX aged-EtOH, XX aged-CON, XX adult-EtOH, XX adult-CON):
  - subject: individual id number
  - diet: treatment with ethanol diet (EtOH) or control diet (CON)
  - age: age group (aged or adult) 
  - sex
  - cohort: cohort id
  - timepoint: time of tissue collection in days post-EtOH
  - dose_01 to dose_6: behavioral intoxication scores for each dosing session
- **dose.csv**: Contains ethanol dose (g/kg) given in each dosing session (every 8 h) with the following variables (n = XX):
  - subject: individual id number
  - diet: treatment with ethanol diet (EtOH) or control diet (CON)
  - age: age group (aged or adult) 
  - sex
  - cohort: cohort id
  - timepoint: time of tissue collection in days post-EtOH
  - dose_01 to dose_6: ethanol dose (g/kg) for each dosing session
- **BEC.csv**: Contains blood ethanol concentrations determined from tail blood collected 90 min following the 6th dose of ethanol (n = XX):
  - subject: individual id number
  - diet: treatment with ethanol diet (EtOH) or control diet (CON)
  - age: age group (aged or adult) 
  - sex
  - cohort: cohort id
  - timepoint: time of tissue collection in days post-EtOH
  - run_01, run_02, run_03: BEC measurements run in triplicate
- **OLD_subjects.csv**: Contains meta data for analysis with the following variables:
  - subject: individual id number
  - diet: treatment with ethanol diet (EtOH) or control diet (CON)
  - age: age group (aged or adult) 
  - sex
  - cohort: cohort id
  - timepoint: time of tissue collection in days post-EtOH
- **<Iba1/MHCII data>.csv**: Contains output of Imaris (Iba1+ cell counts, MHCII+ cell counts, MHCII+/Iba1+ of total Iba1+ cell counts) with the following variables:
  - Slice: Image name
  - Count: Iba1+ cell count
- **<Iba1/CD68 data>.csv**
- **<Vimentin data>.csv**


NOTES:
- All data files are in comma separated value (".csv") format.

## ***data/results*** Directory
The ***data/results*** directory contains summary statistics and Welch's t-tests conducted comparing the effects of age (adult vs aged) on the following ethanol binge metrics: blood ethanol concentration (bec), dose of ethanol (dose), and behavioral intoxication (intoxication) using {rstatix}. It also has the results of two-way ANOVAs and pairwise comparisons conducted on the effects of age (adult vs aged) and diet (ethanol vs control) on Iba1+ (microglia) cell counts and XXX using {rstatix}, {emmeans}, and {afex}. These files have the following self explanatory names:
- **bec_summary.csv**
- **bec_ttest.csv**
- **dose_summary.csv**
- **dose_ttest.csv**
- **intoxication_summary.csv**
- **intoxication_ttest.csv**

## References
Data analysis was conducted in RStudio v2023.12.1.402 (Posit team, 2024) with R v4.2.2 (R Core Team, 2022) using rstatix (Kassambara, 2022), afex (Singmann et al., 2023), and emmeans (Lenth, 2022) packages with visualization in Prism v10.0.3 (GraphPad).
- Kassambara A (2022). _rstatix: Pipe-Friendly Framework for Basic
  Statistical Tests_. R package version 0.7.1,
  <https://CRAN.R-project.org/package=rstatix>.
- Lenth R (2022). _emmeans: Estimated Marginal Means, aka Least-Squares
  Means_. R package version 1.8.3,
  <https://CRAN.R-project.org/package=emmeans>.
- Posit team (2024). RStudio: Integrated Development Environment for R.
  Posit Software, PBC, Boston, MA. URL http://www.posit.co/.
- R Core Team (2022). R: A language and environment for statistical
  computing. R Foundation for Statistical Computing, Vienna, Austria. URL
  https://www.R-project.org/.
- Singmann H, Bolker B, Westfall J, Aust F, Ben-Shachar M (2023). _afex:
  Analysis of Factorial Experiments_. R package version 1.3-0,
  <https://CRAN.R-project.org/package=afex>.
