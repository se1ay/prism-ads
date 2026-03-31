# PRISM-Ads artifact

This repository contains an anonymous research artifact for a study on rule-based auditing of persuasive-risk signals in LLM-generated advertising copy.

The artifact is organized around frozen benchmark data, scored outputs, external validation data, final analysis tables, and final paper figures. It is intended for inspection and reproducibility review rather than as a production software package.

## Repository layout

```text
prism-ads/
├─ README.md
├─ .gitignore
├─ requirements.txt
├─ notebooks/
│  └─ 01_prism_ads_pipeline.ipynb
├─ configs/
│  ├─ config_final.json
│  └─ benchmark_manifest.json
├─ data/
│  ├─ all_generated.csv
│  ├─ scored_all.csv
│  ├─ scored_plus_judge.csv
│  ├─ external_known_groups_scored.csv
│  ├─ external_known_groups_filled.csv
│  ├─ selection_rules_template.csv
│  ├─ working_lexicon.csv
│  ├─ lexicon_summary.csv
│  └─ pattern_smoke_test_results.csv
├─ results/
│  ├─ summary_by_model_regime.csv
│  ├─ regime_contrasts_bootstrap_holm.csv
│  ├─ hypothesis_ready_contrasts.csv
│  ├─ fixed_effects_clustered_coefficients.csv
│  ├─ fixed_effects_model_metadata.csv
│  ├─ variance_partitioning_anova.csv
│  ├─ rule_vs_judge_agreement.csv
│  ├─ bland_altman_ppi.csv
│  ├─ bland_altman_cri.csv
│  ├─ bland_altman_tsi.csv
│  ├─ external_validation_stats.csv
│  ├─ external_validation_summary.csv
│  ├─ external_validation_quality_report.csv
│  ├─ cue_overlap_flags.csv
│  ├─ cue_presence_correlation.csv
│  └─ cue_density_correlation.csv
├─ figures/
│  ├─ figure_1_PPI_regime_model.pdf
│  ├─ figure_2_external_validation.pdf
│  └─ figure_3_cue_heatmap.pdf
└─ docs/
   ├─ runtime_notes.md
   └─ data_dictionary.md
```

## What is included

- A frozen benchmark grid describing the planned prompt design.
- Frozen generated texts and rule-based scored outputs.
- A frozen external validation set with scored public texts.
- A judged subset embedded in `scored_plus_judge.csv`.
- Final summary tables, inferential outputs, agreement diagnostics, and figure files.

## Suggested review path

For a quick audit:
1. Read `configs/benchmark_manifest.json`.
2. Inspect `docs/data_dictionary.md`.
3. Review the core frozen files in `data/`.
4. Check the final tables in `results/`.
5. Open the final figures in `figures/`.

## Reproducibility note

The repository is structured so that most reported tables and figures can be regenerated from the frozen CSV files without rerunning text generation.

## Sanitization note

This artifact was prepared for anonymous review. User-specific paths, names, journal-specific text, and working-directory details were intentionally removed.
