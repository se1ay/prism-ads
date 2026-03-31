# Runtime notes

## Purpose
This file summarizes the execution assumptions for the anonymous review artifact.

## Environment assumptions
- Python 3.10+ is recommended.
- The notebook was originally developed in a Colab-style environment.
- GPU access is useful for generation and optional for table/figure regeneration from frozen CSV outputs.

## What is required to reproduce the final artifact
The repository is designed so that the frozen CSV files can be used to regenerate the reported tables and figures without rerunning large-scale text generation.

Recommended workflow:
1. Create a fresh Python environment.
2. Install the packages listed in `requirements.txt`.
3. Place the repository files in a single working directory.
4. Open `notebooks/01_prism_ads_pipeline.ipynb`.
5. Prefer the analysis and figure-generation sections if the goal is to reproduce the frozen outputs from CSV files.

## Generation and scoring settings recorded for the frozen artifact
- Base seed: `20260318`
- Temperature: `0.35`
- Top-p: `0.92`
- Max new tokens: `120`
- Templates per regime-category cell: `3`
- Replicates per template in the final artifact: `8`

## Planned versus frozen final scope
- The planned benchmark grid contains `1728` rows across `3` generation models.
- The frozen final artifact contains `1152` generated and scored rows across `2` generation models.
- The final judged subset contains `96` rows with non-null judge outputs.
- The external validation file contains `100` scored public texts.

## File-use guidance
- Use `benchmark_grid.csv` for the planned design.
- Use `all_generated.csv` for generated texts.
- Use `scored_all.csv` for the frozen rule-based scores.
- Use `scored_plus_judge.csv` for the subset with judge outputs embedded in the same file.
- Use `external_known_groups_scored.csv` for the external validation set.
- Use the `results/` CSV files and `figures/` PDF files as the canonical final outputs for review.

## Sanitization note
This file intentionally excludes user names, institution names, journal names, local paths, access tokens, and drive-mounted paths.
