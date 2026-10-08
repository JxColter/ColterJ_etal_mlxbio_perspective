# Colter et al. In Silico Biology Perspective
## Comparative Benchmark Assessment of Virtual Cell Models (v1.8.5)

This repository contains the harmonized benchmark evidence, STATE analysis data, and figure-generation scripts used to evaluate current virtual cell and perturbation-response modeling approaches across published single-cell benchmarking studies.

The repository was developed to support the analyses presented in Figure 3 of the accompanying perspective manuscript.

---

# Repository Structure

```text
.
├── Data
│
│   ├── harmonized_1_5_1
│   │   ├── performance.csv
│   │   ├── performance_additional.csv (optional)
│   │   ├── metrics.csv
│   │   ├── baselines.csv
│   │   ├── studies.csv
│   │   ├── coverage.csv
│   │   └── calibration.csv
│   │
│   └── state_1_8
│       ├── text_values.csv
│       ├── figure_values.csv
│       ├── S1.csv
│       ├── S2.csv
│       ├── S3.csv
│       └── extracted source materials
│
├── Scripts
│   └── agreement_analysis_1_8_5.py
│
├── Analysis
│   └── agreement_analysis_1_8_5
│       ├── figures
│       ├── tables
│       ├── inputs.json
│       ├── methods.txt
│       └── output summaries
│
└── README.md
```

---

# Objective

A growing number of virtual cell and perturbation-response models have been proposed, including:

- Transformer-based foundation models
- Autoencoder-based perturbation models
- Graph-based approaches
- State-space and transition models
- Transfer-learning frameworks

Because these models are evaluated using different datasets, prediction tasks, and performance metrics, direct comparison is difficult.

This framework provides a harmonized benchmark synthesis across published studies while preserving the original evaluation context of each benchmark.

---

# Evaluation Domains

Individual benchmark metrics are grouped into four high-level assessment domains:

| Domain | Purpose |
|----------|----------|
| Expression Fit | Agreement with observed transcriptional responses |
| Discrimination | Ability to distinguish perturbation-specific responses |
| Distributional Fidelity | Preservation of population-level structure |
| Gene Recovery | Recovery of differential expression signals |

Domain mappings are explicitly defined in the metric dictionaries contained within the repository.

---

# Figure 3

## Figure 3a

Published benchmark models assessed across:

- Context transfer
- Combination prediction

Each model is evaluated using:

- Individual benchmark observations (small points)
- Domain medians (large markers)
- Summed domain scores

Scores are displayed separately for:

- Expression fit
- Discrimination
- Distribution
- Gene recovery

The summed-domain panel represents the aggregate of available domain-level standings.

---

## Figure 3b

STATE was evaluated separately from the benchmark ranking framework.

Two categories of evidence are shown:

### Context Transfer

Published results reported as percentage improvements relative to comparator models.

Metrics include:

- Pearson delta
- Perturbation discrimination
- Differential expression overlap

### Drug Combinations

Published performance reported using native synergy metrics:

- BLISS correlation
- ZIP correlation

These values are visualized directly from published evaluations and are not transformed into benchmark-relative rankings.

---

# Benchmark Harmonization Method

For benchmark studies, metrics are first oriented so that higher scores consistently indicate better performance.

Within each benchmark evaluation unit:

```text
Best model      = 1.0
Worst model     = 0.0
Intermediate    = relative standing
```

Relative standings are calculated independently for each:

- study
- dataset
- task
- split
- evaluation unit

No rankings are pooled across studies.

Domain scores are calculated only when all required metrics for that domain are available.

---

# STATE Analysis

STATE results are not incorporated into the benchmark ranking framework.

Instead:

- Context-transfer evaluations are displayed as reported percentage improvements relative to comparator models.
- Drug-combination evaluations are displayed using reported BLISS and ZIP correlations.

This avoids converting fundamentally different evaluation paradigms into a single synthetic score.

---

# Important Limitations

1. Relative standing is not equivalent to biological accuracy.

2. Benchmark-specific rankings do not imply superiority across all tasks.

3. Missing values are never imputed.

4. STATE context-transfer gains and drug-combination correlations should not be directly compared with benchmark ranking scores.

5. Architectural descriptions and qualitative claims are never converted into performance scores.

6. Distributional fidelity is reported only when explicit quantitative evidence is available.

7. Benchmark evaluations remain dependent on dataset choice, prediction task, and metric selection.

---

# Reproducibility

Generate all figures and tables using:

```bash
python Scripts/agreement_analysis_1_8_5.py
```

Outputs are written to:

```text
Analysis/agreement_analysis_1_8_5
```

All generated tables, figures, manifests, and provenance information are recreated during execution.

---

# Version

Current release:

```text
v1.8.5
```

Associated manuscript:

```text
Colter et al.
In Silico Biology Perspective
```

This repository is intended as a quantitative synthesis and visualization framework for comparative assessment of current virtual cell modeling approaches rather than as a universal model leaderboard.
