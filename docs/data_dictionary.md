# Data dictionary

This document lists the main files expected in the anonymous artifact and briefly describes their purpose and key fields.

## Core configuration files

### `configs/config_final.json`
Sanitized summary of the final execution settings used for the frozen artifact.

### `configs/benchmark_manifest.json`
Planned-versus-final benchmark counts derived from the frozen files.

## Core data files

### `data/benchmark_grid.csv`
Planned benchmark grid.

Key columns:
- `row_id`: unique row identifier for the planned prompt row.
- `category_key`: product category code.
- `product_name`: product label used in the prompt template.
- `audience`: intended audience descriptor.
- `benefit_anchor`: central product-benefit anchor.
- `regime_key`: prompt-regime code.
- `regime_label`: human-readable regime label.
- `template_idx`: template index within regime-category cell.
- `template_key`: template identifier.
- `prompt_id`: prompt identifier.
- `model_key`: planned generation model.
- `replicate`: planned replicate index.
- `generation_seed_planned`: planned seed for generation.
- `prompt_text`: prompt text supplied to the generation model.

### `data/all_generated.csv`
Generated texts for the frozen final artifact.

Key columns:
- All design columns from `benchmark_grid.csv`
- `generated_text`: model-generated advertising copy.
- `n_words_generated`: generated word count as recorded at export time.
- `generation_seed`: seed recorded at generation time.
- `generated_at_utc`: UTC timestamp recorded for the generation row.

### `data/scored_all.csv`
Rule-based scored outputs for the frozen final artifact.

Key columns:
- All columns from `all_generated.csv`
- `n_words`: word count used for scoring normalization.
- `negation_flags`: marker for negation-sensitive logic.
- For each cue family:
  - `*_count`
  - `*_present`
  - `*_density_100w`
  - `*_weighted`
- Aggregate indices:
  - `PPI_unweighted`, `CRI_unweighted`, `TSI_unweighted`
  - `PPI_weighted`, `CRI_weighted`, `TSI_weighted`
  - `PPI_100w`, `CRI_100w`, `TSI_100w`

Cue families represented in `scored_all.csv`:
- `temporal_urgency`
- `scarcity_marking`
- `fear_loss_framing`
- `coercive_cta`
- `authority_evoking`
- `social_proof`
- `certainty_guarantee`
- `superiority_performance`
- `transparency_supporting`

### `data/scored_plus_judge.csv`
Scored outputs with the judged subset embedded in the same file.

Additional key columns:
- `judge_model`
- `judge_seed`
- `judge_raw`
- `judge_temporal_urgency`
- `judge_scarcity_marking`
- `judge_fear_loss_framing`
- `judge_coercive_cta`
- `judge_authority_evoking`
- `judge_social_proof`
- `judge_certainty_guarantee`
- `judge_superiority_performance`
- `judge_transparency_supporting`
- `judge_comment`
- `judge_PPI`
- `judge_CRI`

Rows without judge outputs remain present so the file aligns row-for-row with `scored_all.csv`.

### `data/external_known_groups_filled.csv`
Frozen external validation source file before scoring.

Key columns:
- `group`: validation group label.
- `source_type`: broad source type.
- `source_org`: source organization label.
- `source_url`: source URL.
- `text`: extracted text scored by the audit.
- `selection_rule_id`: frozen rule identifier.
- `include`: inclusion flag.
- `notes`: manual notes.

### `data/external_known_groups_scored.csv`
Rule-based scores for the frozen external validation set.

Key columns:
- Source metadata from `external_known_groups_filled.csv`
- `n_words`
- Cue-family `*_count`, `*_present`, `*_density_100w`
- Aggregate indices:
  - `PPI_unweighted`, `CRI_unweighted`, `TSI_unweighted`
  - `PPI_100w`, `CRI_100w`, `TSI_100w`

### `data/selection_rules_template.csv`
Frozen mapping between selection-rule identifiers and group targets.

### `data/working_lexicon.csv`
Included cue patterns used by the rule-based audit.

Key columns:
- `cue_id`
- `domain`
- `cue_family`
- `pattern`
- `example_phrase`
- `source_bucket`
- `source_ref`
- `rationale`
- `weight`
- `review_status`
- `include`

### `data/lexicon_summary.csv`
Cue-family level summary of the lexicon.

### `data/pattern_smoke_test_results.csv`
Smoke-test outcomes used to check for obvious false-positive behavior in benign contexts.

## Results files

### `results/summary_by_model_regime.csv`
Descriptive statistics by model and prompt regime.

### `results/regime_contrasts_bootstrap_holm.csv`
Pairwise regime contrasts with bootstrap mean differences and Holm-adjusted p-values.

### `results/hypothesis_ready_contrasts.csv`
Preformatted confirmatory contrasts for direct manuscript use.

### `results/fixed_effects_clustered_coefficients.csv`
Cluster-robust fixed-effects coefficient table.

### `results/fixed_effects_model_metadata.csv`
Model formula and fit metadata for each outcome.

### `results/variance_partitioning_anova.csv`
ANOVA-style variance partitioning summary with partial eta-squared values.

### `results/rule_vs_judge_agreement.csv`
Agreement summary between rule-based indices and judge outputs for the judged subset.

### `results/bland_altman_ppi.csv`
### `results/bland_altman_cri.csv`
### `results/bland_altman_tsi.csv`
Pairwise mean-versus-difference values used to draw Bland–Altman plots.

Each file contains:
- `mean_pair`
- `diff`

### `results/external_validation_stats.csv`
Inferential comparison of problematic versus reference texts in the external validation set.

### `results/external_validation_summary.csv`
Descriptive statistics by external validation group.

### `results/external_validation_quality_report.csv`
Quality-control summary for the external validation sample.

### `results/cue_overlap_flags.csv`
High-overlap cue-pair flags derived from within-benchmark cue correlations.

### `results/cue_presence_correlation.csv`
Cue-family correlation matrix using binary presence indicators.

### `results/cue_density_correlation.csv`
Cue-family correlation matrix using per-100-word densities.

## Figure files

### `figures/figure_1_PPI_regime_model.pdf`
Final regime-by-model PPI figure.

### `figures/figure_2_external_validation.pdf`
Final external validation group-means figure.

### `figures/figure_3_cue_heatmap.pdf`
Final cue-density heatmap figure.

## Notes
- File names in this dictionary follow the cleaned repository structure rather than the original working directory layout.
- This document intentionally excludes personal identifiers and local path metadata.
