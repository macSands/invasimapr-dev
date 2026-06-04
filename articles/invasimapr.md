# Getting started with invasimapr

## Overview

invasimapr is an R package to assess species and trait invasiveness and
site invasibility by visualising trait dispersion and computing invasion
fitness.

The package implements a network invasibility framework that decomposes
invasion fitness into three components:

- **Abiotic suitability** ($`r^{(z)}_{is}`$): how well the environment
  at site $`s`$ suits invader $`i`$.
- **Niche crowding** ($`C^{(z)}_{is}`$): how much functional overlap
  invader $`i`$ has with the resident community at site $`s`$.
- **Resident competition** ($`S^{(z)}_{is}`$): how saturated the
  resident community is at site $`s`$.

## Installation

Install the development version from GitHub:

``` r

# install.packages("remotes")
remotes::install_github("macSands/invasimapr-dev")
```

## Workflow

The core workflow consists of eight steps, each returning an updated
`invasimapr_fit` container:

``` r

library(invasimapr)

# Step 1: Prepare inputs from occurrence, trait and environmental data
fit <- prepare_inputs(
  occ_long   = my_occurrences,
  trait_wide  = my_traits,
  env_wide    = my_environment
)

# Step 2: Simulate hypothetical invader profiles
fit <- simulate_invaders(fit, n_inv = 50, method = "columnwise")

# Step 3: Trait space and crowding
fit <- prepare_trait_space(fit)

# Step 4: Model resident abundances
fit <- model_residents(fit)

# Step 5: Learn trait-dependent sensitivities
fit <- learn_sensitivities(fit)

# Step 6: Predict invader predictors
fit <- predict_invaders(fit)

# Step 7-8: Compute invasion fitness and establishment probability
fit <- predict_establishment(fit, option = "C")

# Summarise invasiveness and invasibility
fit <- summarise_results(fit)
```

## Key functions

| Function | Purpose |
|----|----|
| [`prepare_inputs()`](https://b-cubed-eu.github.io/invasimapr/reference/prepare_inputs.md) | Assemble community, trait and environmental matrices |
| [`simulate_invaders()`](https://b-cubed-eu.github.io/invasimapr/reference/simulate_invaders.md) | Generate hypothetical invader trait profiles |
| [`prepare_trait_space()`](https://b-cubed-eu.github.io/invasimapr/reference/prepare_trait_space.md) | Compute trait space, convex hull, and crowding |
| [`model_residents()`](https://b-cubed-eu.github.io/invasimapr/reference/model_residents.md) | Fit GLMMs to resident abundance |
| [`learn_sensitivities()`](https://b-cubed-eu.github.io/invasimapr/reference/learn_sensitivities.md) | Estimate trait-dependent sensitivity slopes |
| [`predict_invaders()`](https://b-cubed-eu.github.io/invasimapr/reference/predict_invaders.md) | Project invaders into the resident model space |
| [`predict_establishment()`](https://b-cubed-eu.github.io/invasimapr/reference/predict_establishment.md) | Compute invasion fitness and map to probability |
| [`summarise_results()`](https://b-cubed-eu.github.io/invasimapr/reference/summarise_results.md) | Summarise invasiveness and invasibility |

## Further reading

For detailed tutorials with real data, see the package articles on the
[documentation website](https://b-cubed-eu.github.io/invasimapr/):
Introduction, Step-by-step Workflow, Clustering and risk scenarios,
Invasion fitness synthesis, and Computing invasion fitness.

## Acknowledgments

This software was developed with funding from the European Union’s
Horizon Europe Research and Innovation Programme under grant agreement
ID No [101059592](https://doi.org/10.3030/101059592).
