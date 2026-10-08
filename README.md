# Chicken Comb Mass QTL Mapping

An R/qtl analysis of chicken comb mass in an F8 advanced intercross between red junglefowl and White Leghorn chickens, completed for the Genome Analysis practical.

This is my analysis for one the computer exercise sessions, QTL Mapping, done as part of the course of [Genome analysis BK0003 HT2026, 15 ECT credits](https://www.slu.se/en/student-web/studies/courses-and-programmes/course-search/kurser/g/genome-analysis/), at SLU (Swedish University of Agricultural Sciences), Uppsala, Sweden, autumn 2026.

The project uses **Quarto** for the analysis report, **renv** for R package management, and **Git** for version control.

## Objectives

- Inspect phenotype distributions and genotype missingness.
- Check marker linkage, order, and the genetic map.
- Identify potentially erroneous genotype calls.
- Compare QTL scans with and without sex and body-weight adjustment.
- Assess scan significance using permutation tests.
- Estimate QTL effects and refine candidate positions.

## Project files

| File or directory | Purpose |
|----|----|
| `comb-qtl.qmd` | Complete analysis, figures, and interpretations |
| `_quarto.yml` | Quarto project configuration |
| `data/raw/QTL_group_work.csv` | Original practical dataset |
| `renv.lock` | Recorded R version and package dependencies |
| `.Rprofile` | Activates the project’s renv environment |
| `renv/` | renv configuration and activation files |
| `_output/` | Rendered reports |
| `README.md` | Project overview and reproduction instructions |

## Data and analysis

The supplied dataset contains **572 individuals** and **40 markers** on chromosomes **1 and 3**. Phenotypes include comb mass, sex, and body weight at 212 days.

Following map diagnostics, marker `Gg_rs15777012` was provisionally excluded from the working map. Five genotype calls flagged by error-LOD analysis were retained because errors were not independently confirmed.

The QTL scans use the same **440 individuals** with complete comb-mass, sex, and body-weight records. Four Haley–Knott scans compare no covariates, sex alone, body weight alone, and both covariates. Each scan uses **1,000 permutations** for significance assessment.

A two-QTL model includes sex and body weight, estimates additive and dominance effects, and refines candidate positions.

## Main findings

- Chromosome 3 shows the strongest evidence for a comb-mass QTL. Its fully adjusted scan peaks at **12.763 cM**, with **LOD 21.448**.
- Adjustment for sex and body weight substantially increases the chromosome 3 peak LOD compared with the unadjusted scan.
- Joint refinement retains the chromosome 3 position. Its refined additive-effect estimate is approximately **4.141 g**, corresponding to an adjusted BB–AA difference of **8.282 g**.
- The chromosome 1 candidate is weaker and more sensitive to the model. Refinement moves its position from **125 to 93 cM**.
- The refined model explains approximately **83.359%** of observed comb-mass variation, including the contributions of both covariates.

Full results and interpretation are presented in `comb-qtl.qmd`.

## Reproduce the report

Install R, RStudio, and Quarto. Open the project in RStudio, then restore the recorded R packages from the R Console:

``` r
renv::restore()
renv::status()
```

Render the HTML report from the project root in the terminal:

``` bash
quarto render comb-qtl.qmd --to html
```

The report is written to `_output/comb-qtl.html`. With `embed-resources: true`, figures and supporting resources are embedded in the HTML file.

For PDF output, a LaTeX installation is also required:

``` bash
quarto render comb-qtl.qmd --to pdf
```

Rendering reruns the analysis, including the permutation tests. Random seeds are specified in the analysis code. Section 12 records the dependency status and R session information.

## Interpretation limits

The F8 advanced intercross is analyzed using an **F2 approximation**, and the genetic map remains provisional. Family structure is not modeled.

Permutation thresholds apply to the supplied chromosomes **1 and 3**, rather than the complete genome. Nominal tests after position refinement do not account for selecting positions using the same data.

Founder-line correspondence of AA and BB has not been confirmed. The detected QTL therefore do not establish founder-specific effect directions or identify causal genes or variants.

## Source materials

- *QTL MAPPING practical – Comb Data*: assignment and population description.
- *QTL_group_work.csv*: supplied genotype and phenotype data.

## Acknowledgments

This project was completed as part of a functional genomics practical. The data and teaching workflow were supplied with the course materials.

*Supervising instructor*: **Dominic Wright**, Professor, HBIO, Molecular Genetics and Bioinformatics

## Author

**Dakouri Kobri**\
Data Science, AI/ML, Bioinformatics, Pharmacology, Toxicology\
& Health Science Enthusiast\
[LinkedIn](https://www.linkedin.com/in/dakouri-m-kobri-009192208/)

## Resources

- [Quarto](https://quarto.org/)
- [renv](https://rstudio.github.io/renv/)
