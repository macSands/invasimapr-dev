# invasimapr 0.1.0

- Initial release of the invasimapr package.
- Core workflow functions for invasion fitness computation:
  `prepare_inputs()`, `simulate_invaders()`, `standardise_model_inputs()`,
  `prepare_trait_space()`, `model_residents()`, `learn_sensitivities()`,
  `predict_invaders()`, `predict_establishment()`, `summarise_results()`.
- Trait space visualisation via `compute_trait_space()` and
  `compute_centrality_hull()`.
- Resident crowding and site saturation metrics via
  `compute_resident_crowding()` and `compute_site_saturation()`.
- Multiple invasion fitness options (A-E) via `compute_invasion_fitness()`.
- Establishment probability mapping via
  `compute_establishment_probability()`.
- Species invasiveness and site invasibility summaries via
  `summarise_invasiveness_invasibility()`.
