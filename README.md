## Subsampling Stability & Sample Size Optimization for Spatial Material Measurements

Material quality can vary across the surface of a specimen (e.g., sheet, film, or laminate). When measuring physical properties across multiple positions on each specimen, the number of measurement locations determines how reliably the specimen-level mean can be estimated.

This notebook demonstrates a practical, data-driven method to determine **how many spatial measurement points per specimen are truly required** — enabling confident mean estimation without oversampling.

---

### Objective

Use oversampled specimens (15 spatial measurements per specimen) to:

- Assess the stability of specimen mean estimates as sample size decreases  
- Identify the minimum number of measurement points that achieve a target error tolerance  
- Quantify the trade-off between sampling effort and statistical confidence  

---

### Method Overview

1. Load oversampled specimen data (real or synthetic)
2. Generate subsamples of size 1 … N for each specimen (no replacement)
3. Compare subsample means to the full-specimen reference mean
4. Compute:
   - Absolute and percent deviation from true mean  
   - Confidence intervals across bootstrap draws  
   - Stability metrics against desired accuracy thresholds
5. Determine the **minimum viable sampling density**
6. Visualize subsampling stability curves to support decisions

This approach uses **resampling statistics** and **replicate structure** to empirically determine sampling sufficiency — without relying solely on theoretical formulas.

---

### Why This Matters

In biomaterials research, manufacturing quality control, and experimental science, measurement time and lab capacity are finite. Calibrating sampling density to actual specimen variability helps:

- Reduce unnecessary measurements
- Improve throughput without compromising data quality
- Set evidence-based sampling standards
- Build efficient, scalable material testing workflows

This workflow supports **data-driven sampling design**, especially when spatial variability exists but optimal sampling density is unknown.

---

### Repository Contents

| File | Description |
|------|-------------|
| `Decomposition_anonymized_v4.Rmd` | Main analysis notebook (anonymized) |
| `synthetic_sheet_sampling_20x15.csv` | Synthetic dataset for demonstration |
| `README.md` | Project documentation |

---

### Requirements

- R  
- tidyverse libraries (`dplyr`, `ggplot2`, `purrr`, `tibble`)

---

### Outputs

- Recommended number of spatial measurements per specimen  
- Bootstrap-based sampling stability curves  
- Summary tables supporting sampling decisions  

---

### Notes

- Real data is **not included**; a synthetic oversampled dataset is provided to demonstrate the workflow.
- This approach generalizes to any scenario involving multi-point specimen measurements (density, thickness, modulus, optical properties, etc.).

---
