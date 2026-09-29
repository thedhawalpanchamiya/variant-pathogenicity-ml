# Interpretable Machine Learning for Genetic Variant Pathogenicity Prediction

## Overview

This project investigates whether machine learning can be used to predict the pathogenicity of genetic variants using sequence-derived, molecular, and population-level features.

The project focuses on **interpretable linear machine learning models**, particularly logistic regression and its regularized variants, rather than relying immediately on complex black-box models.

The central idea is to transform information associated with a genetic variant into a numerical feature representation and use statistical learning to estimate the probability that the variant is pathogenic.

> **Core problem:**  
> Genetic variant + biological features → pathogenicity prediction

The project is designed as an educational and exploratory computational biology study and is **not intended for clinical diagnosis**.

---

## Research Question

> **Can interpretable linear machine learning models predict the pathogenicity of genetic variants from sequence, molecular, and population-level features?**

The project also investigates which features contribute most strongly to the model's predictions.

---

## Objectives

The main objectives of this project are:

- Collect genetic variant information from publicly available databases.
- Construct a clean, reproducible variant-level dataset.
- Represent genetic variants using numerical biological and molecular features.
- Incorporate population-level information such as allele frequency.
- Investigate the predictive contribution of existing computational predictors.
- Train interpretable linear classification models.
- Compare different forms of regularization.
- Evaluate model performance using appropriate classification metrics.
- Analyze model coefficients to understand feature contributions.
- Relate computational predictions to biological interpretation.
- Document limitations and potential sources of bias.

---

## Conceptual Workflow

```text
                         PUBLIC DATABASES
                              │
                              ▼
                       ┌──────────────┐
                       │   ClinVar    │
                       │              │
                       │ Variants +   │
                       │ clinical     │
                       │ significance │
                       └──────┬───────┘
                              │
                              ▼
                     DATA CLEANING & QC
                              │
                              ▼
                    VARIANT REPRESENTATION
                              │
              ┌───────────────┼────────────────┐
              │               │                │
              ▼               ▼                ▼
       DNA-level data   Protein-level    Gene/sequence
                           data             features
              │               │                │
              └───────────────┼────────────────┘
                              ▼
                    FEATURE ENGINEERING
                              │
              ┌───────────────┼────────────────┐
              │               │                │
              ▼               ▼                ▼
       Molecular       Population-level   Computational
        features          features          predictors
              │               │                │
              └───────────────┼────────────────┘
                              ▼
                       FEATURE MATRIX (X)
                              │
                              │
                       TARGET VECTOR (y)
                              │
                              ▼
                  TRAIN / VALIDATION / TEST
                              │
                              ▼
                       PREPROCESSING
                              │
                              ▼
                  ┌─────────────────────┐
                  │ Logistic Regression │
                  └──────────┬──────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
             L1             L2         Elastic Net
        Regularization  Regularization  Regularization
              │              │              │
              └──────────────┼──────────────┘
                             ▼
                      MODEL EVALUATION
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
           ROC-AUC         PR-AUC       F1 / Recall
              │              │              │
              └──────────────┼──────────────┘
                             ▼
                       INTERPRETATION
                             │
                    ┌────────┴────────┐
                    ▼                 ▼
              Coefficient        Biological
               analysis        interpretation
                    │                 │
                    └────────┬────────┘
                             ▼
                       FINAL ANALYSIS
