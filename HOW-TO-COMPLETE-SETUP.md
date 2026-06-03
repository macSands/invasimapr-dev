# invasimapr: Steps to Complete B-Cubed Compliance

This document lists everything you need to run locally in RStudio to finish
aligning the package with the B-Cubed Software Development Guide.

---

## What has already been done (by Claude)

| File | Status |
|---|---|
| `DESCRIPTION` | One-sentence Description, authors+ORCID, institution cph, Imports (no sp), BugReports URL, no Depends |
| `LICENSE` + `LICENSE.md` | MIT with Stellenbosch University as copyright holder |
| `.gitignore` | `.DS_Store` under `# Mac OS`, standard R entries |
| `.Rbuildignore` | Excludes LICENSE.md, README.Rmd, .github, .zenodo.json, CITATION.cff, vignettes/articles, HOW-TO |
| `CITATION.cff` | Name, ORCID, package metadata, no doi/date-released |
| `.github/CONTRIBUTING.md` | Contribution guidelines |
| `NEWS.md` | v0.1.0 changelog |
| `.zenodo.json` | B-Cubed community `b3` + grant `101059592` |
| `inst/CITATION` | R-specific citation file |
| `README.Rmd` + `README.md` | Logo, badges, one-paragraph description, install, example, meta, EU acknowledgment |
| `_pkgdown.yml` | URL set, bootstrap 5 |
| `R/compute_centrality_hull.R` | Removed sp; sf is sole geometry backend |
| `R/get_trait_data.R` | Replaced `print()` with `graphics::plot()` guarded by `interactive()` |
| `R/compute_trait_space.R` | Replaced `print()` with `graphics::plot()` guarded by `interactive()` |
| `R/utils_internal.R` | Added `globalVariables()` for NSE, `@importFrom stats kmeans`, `@importFrom utils URLencode tail` |
| `R/site_varying_alpha_beta_gamma.R` | Changed `ranef()` to `glmmTMB::ranef()` |
| `R/predict_establishment.R` | Fixed switch partial match |
| `R/prepare_trait_space.R` | Fixed @param mismatch (do_dend vs highlight_level) |
| `R/learn_sensitivities.R` | Fixed corrupted duplicate roxygen block |
| `R/assemble_matrices.R` | Fixed multi-line @importFrom |
| `vignettes/invasimapr.Rmd` | Proper vignette with VignetteIndexEntry |
| `vignettes/articles/` | 5 tutorial Rmds as pkgdown articles (eval=FALSE) |

---

## Step 1: CODE_OF_CONDUCT.md

```r
usethis::use_tidy_coc()
```

Then open `.github/CODE_OF_CONDUCT.md` and replace `codeofconduct@posit.co`
with `b-cubedsupport@meisebotanicgarden.be`.

---

## Step 2: Delete leftover data from vignettes/articles

Manually delete the `_data` folder (I couldn't from the sandbox):

```
vignettes/articles/_data/    <-- delete this entire folder
```

---

## Step 3: Generate documentation

```r
devtools::document()
devtools::document()   # second pass resolves internal cross-references
```

---

## Step 4: R CMD check

```r
devtools::check()
```

Must pass with **0 ERRORs** (B-Cubed MUST).

---

## Step 5: Set up testing

```r
usethis::use_testthat()
usethis::use_test("prepare_inputs")
usethis::use_test("simulate_invaders")
usethis::use_test("compute_trait_space")
usethis::use_test("model_residents")
usethis::use_test("predict_establishment")
usethis::use_test("summarise_results")
```

**B-Cubed requires:** At least 75% code coverage.

---

## Step 6: GitHub Actions

```r
usethis::use_github_action("check-standard", badge = TRUE)
usethis::use_github_action("test-coverage", badge = TRUE)
usethis::use_pkgdown_github_pages()   # also sets up pkgdown deployment action
```

---

## Step 7: Codecov

1. Sign in at https://app.codecov.io/ with GitHub.
2. Add `macSands/invasimapr-dev`.
3. Copy `CODECOV_TOKEN` to repo Settings > Secrets > Actions.

---

## Step 8: codemeta.json

```r
codemetar::write_codemeta()
```

**B-Cubed MUST:** R packages must include `codemeta.json`.

---

## Step 9: Build README

```r
devtools::build_readme()
```

---

## Step 10: Transfer repo to b-cubed-eu (MUST)

The B-Cubed guide requires: "A repository MUST be public and be part of
a GitHub organization (e.g. b-cubed-eu)."

Once ready, transfer from `macSands/invasimapr-dev` to `b-cubed-eu/invasimapr`.
Then update all URLs in:
- `DESCRIPTION` (URL, BugReports)
- `README.Rmd` and `README.md` (badges, install instructions)
- `CITATION.cff` (repository-code, url)
- `_pkgdown.yml` (url)
- `.github/CONTRIBUTING.md` (issue links)

---

## Step 11: GitHub repo settings

1. **Topics:** `r`, `rstats`, `r-package`, `invasive-species`,
   `invasibility`, `trait-dispersion`, `biodiversity`, `b-cubed`
2. **Hide tabs:** Settings > Features > turn off `Wikis` and `Projects`
3. **Branch protection:** Settings > Branches > add rule for `main` >
   "Require a pull request before merging" with "Require approvals"

---

## Step 12: b3doc tutorial conversion

```r
remotes::install_github("b-cubed-eu/b3doc")
library(b3doc)

# You'll need to temporarily set eval=TRUE in each article
# and run them with the package installed, then convert:

rmd_to_md(
  rmd_file = "vignettes/articles/introduction.Rmd",
  md_dir = "output/src/content/docs/software/invasimapr",
  fig_dir = "output/public/software/invasimapr",
  fig_url_dir = "/software/invasimapr/",
  title = "Introduction",
  sidebar_label = "introduction",
  sidebar_order = 1
)

# Repeat for each tutorial (2-5), incrementing sidebar_order
```

Submit output as a PR to https://github.com/b-cubed-eu/documentation.

---

## Step 13: First GitHub release

1. Tag: `0.1.0`
2. Title: `invasimapr 0.1.0`
3. Paste NEWS.md content as release notes.

From release 1.0 onward, also publish on Zenodo (`.zenodo.json` is ready).

---

## Quick checklist

- [ ] CODE_OF_CONDUCT.md created (Step 1)
- [ ] `vignettes/articles/_data/` deleted (Step 2)
- [ ] `devtools::document()` clean (Step 3)
- [ ] `devtools::check()` 0 ERRORs (Step 4)
- [ ] Tests with >= 75% coverage (Step 5)
- [ ] GitHub Actions + pkgdown deployment (Step 6)
- [ ] Codecov connected (Step 7)
- [ ] `codemeta.json` created (Step 8)
- [ ] README.md built from Rmd (Step 9)
- [ ] Repo transferred to b-cubed-eu (Step 10)
- [ ] GitHub settings configured (Step 11)
- [ ] b3doc conversion + PR to docs repo (Step 12)
- [ ] First release published (Step 13)
