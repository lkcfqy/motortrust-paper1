# MotorTrust — Paper 1

Independent repository for **When Healthy-Only Transfer Fails in PMSM Stator-Fault Detection: A Leakage-Resistant Cross-Dataset Evaluation** and the current Journal of Magnetics author-review submission.

Source: [motortrust](https://github.com/lkcfqy/motortrust), commit `0cbfc7e5b2868f482902f16d6d0b0c71f9d01f11`, split on 2026-10-09. Files retain their original relative paths and bytes. Original historical metadata and all frozen results are preserved. The included submission sources and ZIPs contain author contact details, published with the author's explicit permission.

## Contents

- `submission/jom/`: current manuscript, supplementary material, author-review files, figures, audits and source evidence.
- `submission/jeet/`, `paper/`: preserved earlier submission and scientific source material.
- `src/`, `scripts/`, `tests/`, `configs/`, `docs/`, `references/`: Paper 1 code and necessary shared publication utilities.
- `results/`, `data/processed/`: saved Paper 1 experiment outputs and hash-locked processed features.
- `recovery/licenses/`: original dataset attribution and license records.

## Install and verify saved evidence

Use Python 3.12 in a fresh environment:

```sh
python -m venv .venv
.venv/bin/python -m pip install -e ".[dev,publication]"
.venv/bin/python scripts/validate_manuscript_evidence.py --output tmp/reproduction/historical_evidence.json
.venv/bin/python scripts/audit_jom_evidence.py --output tmp/reproduction/jom_evidence.json
.venv/bin/python -m pytest -q tests/test_frozen_artifact_paths.py tests/test_jom_source_contract.py tests/test_fault_baseline.py tests/test_external_seed_sensitivity.py tests/test_external_feature_drift.py tests/test_manuscript_evidence_validation.py
```

These checks inspect saved evidence and do not retrain or repeat a fault reveal. Scientific limits, historical software-version differences, exact signal-level commands and JOM rebuild instructions are in [`submission/jom/Reproducibility_Guide.md`](submission/jom/Reproducibility_Guide.md) and [`submission/jom/QA_Report.md`](submission/jom/QA_Report.md). Rebuilding documents requires the publication renderer and new visual review for changed pages.

## Raw datasets

Raw current signals, MAT files and original source ZIPs are kept out of Git to keep cloning practical. Download the raw-data split archive from [Releases](https://github.com/lkcfqy/motortrust-paper1/releases). The release inventory and SHA-256 checksums describe exactly what was uploaded. Raw data are also available from the official DOI links in the reproducibility guide; third-party attribution and license requirements still apply.

The original code and manuscripts have no independent license declaration in the source repository. Dataset license notices do not grant a new license to project code or manuscripts.


## Download and restore this paper's raw-data Release

Download `raw-data-manifest.json` and all numbered parts from [raw-data-2026-10-09](https://github.com/lkcfqy/motortrust-paper1/releases/tag/raw-data-2026-10-09) into one folder. The committed expected manifest is [`recovery/raw-data-manifest.json`](recovery/raw-data-manifest.json). From this repository root, run:

```sh
python scripts/restore_raw_data.py --parts-dir /path/to/downloaded/assets
```

The standard-library script verifies the downloaded manifest against this repository's expected bytes, every split part, the joined archive, and every raw file before installing data under `data/raw/`. Identical existing files are skipped; different existing files are protected. The raw archive was independently verified in full; the record is [`recovery/raw_archive_verification.json`](recovery/raw_archive_verification.json). `git clone` contains code, papers, processed inputs and saved results; it does not download the raw-data assets.
