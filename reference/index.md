# Package index

## Core workflow

Main pipeline functions, called in sequence.

- [`prepare_inputs()`](https://b-cubed-eu.github.io/invasimapr/reference/prepare_inputs.md)
  : Prepare inputs (assemble and align core tables)
- [`simulate_invaders()`](https://b-cubed-eu.github.io/invasimapr/reference/simulate_invaders.md)
  : Simulate hypothetical invader trait profiles from a resident trait
  pool
- [`prepare_trait_space()`](https://b-cubed-eu.github.io/invasimapr/reference/prepare_trait_space.md)
  : Prepare trait space and resident crowding (no site-z)
- [`model_residents()`](https://b-cubed-eu.github.io/invasimapr/reference/model_residents.md)
  : Resident GLMM and construction of standardized predictors
- [`learn_sensitivities()`](https://b-cubed-eu.github.io/invasimapr/reference/learn_sensitivities.md)
  : Learn sensitivities (alpha_i, beta_i, theta_i / gamma_i) and
  optional site effects
- [`predict_invaders()`](https://b-cubed-eu.github.io/invasimapr/reference/predict_invaders.md)
  : Build standardized invader predictors (r_is_z, C_is_z, S_is_z)
- [`predict_establishment()`](https://b-cubed-eu.github.io/invasimapr/reference/predict_establishment.md)
  : Compute invasion fitness (\\\lambda\\) and optional establishment
  probability (\\P\\)
- [`summarise_results()`](https://b-cubed-eu.github.io/invasimapr/reference/summarise_results.md)
  : Summarise invasiveness and invasibility (tables, maps, rankings)

## Trait space and crowding

Compute trait ordination, convex hulls, centrality and crowding.

- [`compute_trait_space()`](https://b-cubed-eu.github.io/invasimapr/reference/compute_trait_space.md)
  : Shared trait-space construction (Gower + PCoA), resident hull,
  centroid, and density plot
- [`compute_centrality_hull()`](https://b-cubed-eu.github.io/invasimapr/reference/compute_centrality_hull.md)
  : Compute trait-space centrality (robust Mahalanobis) and hull status,
  with visuals
- [`compute_resident_crowding()`](https://b-cubed-eu.github.io/invasimapr/reference/compute_resident_crowding.md)
  : Resident crowding \\C\_{js}\\ via Hellinger composition and
  Gower–Gaussian trait kernel

## Resident modelling

Fit GLMMs to resident abundances and derive predictors.

- [`assemble_matrices()`](https://b-cubed-eu.github.io/invasimapr/reference/assemble_matrices.md)
  : Assemble community matrices for invasion-fitness workflows
- [`standardise_model_inputs()`](https://b-cubed-eu.github.io/invasimapr/reference/standardise_model_inputs.md)
  : Standardise model inputs (no leakage) for residents and invaders
- [`standardise_by_site()`](https://b-cubed-eu.github.io/invasimapr/reference/standardise_by_site.md)
  : Standardize a site-by-species matrix by site (row-wise z) with
  optional robust SD
- [`build_model_formula()`](https://b-cubed-eu.github.io/invasimapr/reference/build_model_formula.md)
  : Flexible formula constructor for residents-only trait–environment
  models
- [`prep_resident_glmm()`](https://b-cubed-eu.github.io/invasimapr/reference/prep_resident_glmm.md)
  : Build residents-by-sites long table and fit the residents-only GLMM
- [`compute_site_saturation()`](https://b-cubed-eu.github.io/invasimapr/reference/compute_site_saturation.md)
  : Compute site-only saturation \\S\_{s}\\ and global z-score
  \\S\_{s}^{(z)}\\

## Sensitivity estimation

Estimate trait-dependent slopes and site-varying effects.

- [`fit_auxiliary_residents_glmm()`](https://b-cubed-eu.github.io/invasimapr/reference/fit_auxiliary_residents_glmm.md)
  : Auxiliary GLMM for trait-varying and site-varying slopes
- [`derive_sensitivities()`](https://b-cubed-eu.github.io/invasimapr/reference/derive_sensitivities.md)
  : Derive trait-varying sensitivities (αᵢ, βᵢ) and abiotic slope (θ,
  Γᵢ)
- [`site_varying_alpha_beta_gamma()`](https://b-cubed-eu.github.io/invasimapr/reference/site_varying_alpha_beta_gamma.md)
  : Site-varying alpha and gamma with trait-dependent beta

## Invader prediction

Build invader predictors and compute invasion fitness.

- [`build_invader_predictors()`](https://b-cubed-eu.github.io/invasimapr/reference/build_invader_predictors.md)
  : Build standardized invader predictors r_is_z, C_is_z, S_is_z
  (expects env/traits frames already projected to model columns)
- [`compute_invasion_fitness()`](https://b-cubed-eu.github.io/invasimapr/reference/compute_invasion_fitness.md)
  : Compute invasion fitness \\\lambda\_{is}\\ for multiple model
  options
- [`compute_establishment_probability()`](https://b-cubed-eu.github.io/invasimapr/reference/compute_establishment_probability.md)
  : Probabilistic establishment from invasion fitness

## Summaries

Summarise invasiveness and invasibility.

- [`summarise_invasiveness_invasibility()`](https://b-cubed-eu.github.io/invasimapr/reference/summarise_invasiveness_invasibility.md)
  : Summaries of invasion fitness: species invasiveness, trait effects,
  and site invasibility

## Data and traits

Retrieve trait data from external sources.

- [`get_trait_data()`](https://b-cubed-eu.github.io/invasimapr/reference/get_trait_data.md)
  : Scrape and Analyze Wikipedia & Trait Data for a Species
