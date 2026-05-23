# Subsampling Stability & Sample Size Optimization for Spatial Material Measurements
[![DOI](https://zenodo.org/badge/1089168157.svg)](https://doi.org/10.5281/zenodo.20358653)

## Summary

This repository presents a practical workflow for estimating the minimum number of spatial measurements required to characterize specimen-level material properties with acceptable accuracy.

Material properties often vary across the surface or volume of a specimen, especially in sheets, films, laminates, biological materials, composites, and other spatially heterogeneous systems. When multiple positions are measured on each specimen, the number of measurement locations directly affects the reliability of the specimen-level mean. Too few measurements can misrepresent the specimen. Too many measurements can waste time, labor, instrument capacity, and sample material.

This workflow uses oversampled specimens to empirically evaluate how specimen-level mean estimates change as fewer spatial measurement points are used. By repeatedly subsampling known oversampled specimens, the analysis identifies the minimum viable sampling density needed to achieve a user-defined error tolerance.

The goal is to support evidence-based sampling design: measuring enough to be confident, but not more than is practically necessary.

---

## Novelty and Scope

This repository presents an applied sampling-design workflow for spatial material measurements. It does **not** claim to introduce a new statistical theory or fundamentally new resampling algorithm.

Related concepts already exist across:

- bootstrap resampling
- subsampling analysis
- measurement system analysis
- statistical quality control
- spatial sampling design
- power and sample-size analysis
- experimental design for materials characterization

The contribution of this repository is an **applied, reproducible workflow** for translating oversampled spatial measurement data into a practical sampling recommendation.

The workflow is designed for situations where the central question is not simply:

> How many total specimens do I need?

but rather:

> How many measurement locations per specimen are needed to estimate each specimen-level mean with acceptable reliability?

This distinction is important in material testing, process development, and quality control because spatial measurement effort is often nested within specimen-level replication. A study may have many specimens, many positions per specimen, or both. This workflow focuses specifically on the within-specimen sampling-density problem.

This repository should be interpreted as:

- a practical resampling workflow
- a technical prototype
- a sampling-design decision aid
- a reproducible example using synthetic demonstration data

It should not currently be interpreted as:

- a universal sample-size formula
- a replacement for study-level power analysis
- a complete spatial statistics framework
- a validated production quality-control standard
- a claim of novelty over existing resampling or sampling-design literature

---

## Objective

Use oversampled specimens to:

- assess the stability of specimen-level mean estimates as measurement density decreases
- identify the minimum number of spatial measurement points that achieve a target error tolerance
- quantify the trade-off between sampling effort and estimation confidence
- support evidence-based measurement standards for heterogeneous material specimens

In the demonstration dataset, each specimen contains 15 spatial measurements. These oversampled measurements are treated as a high-density reference against which smaller subsamples are compared.

---

## Method Overview

The workflow proceeds in six main steps.

### 1. Load oversampled specimen data

The analysis begins with specimens measured at multiple spatial locations. The repository includes a synthetic demonstration dataset with 20 specimens and 15 spatial measurements per specimen.

The same workflow can be applied to real or synthetic data when each specimen has repeated spatial measurements of the same material property.

### 2. Define the full-specimen reference mean

For each specimen, the mean across all available measurement locations is treated as the high-density reference estimate.

This reference mean is not assumed to be a perfect truth. Rather, it is treated as the best available estimate given the oversampled measurement design.

### 3. Generate spatial subsamples

For each specimen, the workflow repeatedly draws subsamples of size 1 through N measurement points without replacement.

For example, if a specimen has 15 total measurement locations, the workflow evaluates subsample sizes from 1 to 15.

### 4. Compare subsample means to the reference mean

For every subsample draw, the workflow compares the subsample mean to the full-specimen reference mean.

The analysis computes:

- absolute deviation from the reference mean
- percent deviation from the reference mean
- bootstrap distributions of estimation error
- confidence intervals across repeated subsampling draws

### 5. Estimate sampling stability

For each candidate sampling density, the workflow summarizes how reliably subsampled means approximate the reference mean.

This can be evaluated using user-defined thresholds such as:

- median absolute error
- 90th or 95th percentile absolute error
- percent of subsamples within a target tolerance
- confidence intervals around expected deviation

### 6. Recommend a minimum viable sampling density

The recommended number of spatial measurements per specimen is the smallest subsample size that satisfies the selected tolerance criterion.

This allows sampling density to be calibrated against observed specimen heterogeneity rather than chosen arbitrarily.

---

## Why This Matters

In biomaterials research, manufacturing quality control, and experimental science, measurement time and lab capacity are finite. Calibrating sampling density to actual specimen variability can help:

- reduce unnecessary measurements
- improve analytical throughput
- avoid under-sampling heterogeneous materials
- set evidence-based measurement standards
- balance confidence against labor and instrument time
- build scalable material testing workflows

This is especially useful when spatial variability exists but the optimal number of measurement locations is unknown.

Rather than relying only on theoretical formulas, the workflow uses empirical resampling from oversampled specimens to estimate how much information is lost as measurement density decreases.

---

## Practical Use Cases

This workflow is most useful when:

- each specimen can be measured at multiple spatial locations
- specimens show spatial heterogeneity
- the specimen-level mean is an important summary statistic
- measurement effort is expensive, slow, destructive, or capacity-limited
- an initial oversampling study can be performed to calibrate future measurement density
- the goal is to create a defensible sampling standard for later experiments

Potential applications include:

- sheet materials
- films and membranes
- laminates
- foams
- composites
- biomaterials
- mycelium-based materials
- coatings
- textiles
- biological tissues
- spatial sensor measurements
- density, thickness, modulus, color, optical, or mechanical-property mapping

---

## Demonstration Synthetic Dataset

The repository includes a synthetic oversampled dataset for demonstration:

```text
synthetic_sheet_sampling_20x15.csv
