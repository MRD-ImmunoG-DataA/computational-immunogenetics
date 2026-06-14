# Research Roadmap

## Computational Immunogenetics and Three-Dimensional TCR Geometry in Colorectal Cancer

---

## 1. Project Introduction

This document describes the scientific and operational roadmap for the project **Computational Immunogenetics and Three-Dimensional Geometry of the T Cell Receptor (TCR)**.

The central goal of this project is to investigate the hypothesis that **geometric and conformational features of the T cell receptor may be associated with differences in the intensity, quality, and type of downstream T cell signaling**.

The biological focus of this project is **colorectal cancer (CRC)**. The working assumption is that specific structural properties of TCRs may contribute to tumor antigen recognition, T cell activation, and the development of anti-tumor immune responses.

This roadmap is designed to ensure that the project is developed according to the following principles:

- computational reproducibility;
- methodological transparency;
- complete documentation of data, code, and analytical decisions;
- suitability for future manuscript development;
- reviewability by other researchers;
- clear separation between completed, ongoing, planned, and out-of-scope activities.

---

## 2. Central Research Hypothesis

The central hypothesis of this project is:

> Three-dimensional changes in TCR architecture, particularly within the CDR3α and CDR3β regions, the angle between the alpha and beta chains, the orientation of the TCR relative to the peptide-MHC complex, and spatial distances between functional domains, may influence downstream T cell signaling patterns and may be associated with functional differences in anti-tumor immune responses, particularly in colorectal cancer.

More specifically, this project investigates whether geometric features of the TCR can provide evidence for differences in:

- the potential intensity of T cell activation;
- the quality of the immune response;
- potential tumor antigen recognition;
- structural distinctions between TCRs with different functional patterns;
- geometric signatures associated with anti-tumor immune responses in CRC.

---

## 3. Research Scope

### 3.1. Main Scope

At the current stage, this project focuses on:

- analysis of three-dimensional TCR and TCR-pMHC structures;
- extraction of data from reliable structural databases, especially the Protein Data Bank (PDB);
- processing of TCR alpha and beta chains;
- identification and extraction of geometric and structural features;
- generation of feature matrices suitable for statistical analysis and machine learning;
- evaluation of associations between structural features and functional annotations, when available;
- biological emphasis on colorectal cancer, when relevant data are accessible.

### 3.2. Out-of-Scope Items at the Current Stage

The following items are not direct objectives of the current phase, unless they are added in later development stages:

- large-scale full molecular dynamics simulations;
- clinical therapeutic design or engineering of TCRs for direct medical use;
- analysis of private patient data without ethical approval;
- definitive prediction of patient treatment response;
- replacement of experimental validation with structural analysis alone;
- clinical conclusions without independent and validated datasets.

---
---

## Phase 4: Reproducibility, Environment Management, and Data Lineage

### 4.1. Phase Goal

The goal of this phase is to ensure that all computational analyses in the project are fully reproducible, transparent, and auditable.

This phase establishes standardized procedures for environment management, version control, computational provenance, and data lineage tracking. These practices ensure that all results generated in later phases can be reliably reproduced and verified.

### 4.2. Reproducibility Requirements

To increase the reproducibility of this project, all stages must be documented clearly and systematically.

Every analysis should be designed so that another researcher can reproduce similar results using the same data, code, and settings.

At each stage, the following items should be recorded:

- data source;
- data retrieval date;
- software and library versions;
- code version or commit hash;
- inclusion criteria;
- exclusion criteria;
- processing parameters;
- statistical or machine learning parameters;
- random seeds used in computational models;
- input and output file structure;
- complete execution path of the pipeline.

### 4.3. Core Files Supporting Reproducibility

The following files should be maintained to support reproducibility, transparency, and project-level documentation:
```text
README.md
requirements.txt
.gitignore
docs/research_roadmap.md
docs/methodology.md
docs/data_dictionary.md
docs/reproducibility_checklist.md
docs/analysis_decisions.md
data/README.md
src/README.md``` ` 


## Phase 5: Extraction of Geometric and Structural TCR Features

### 5.1. Phase Goal

The goal of this phase is to convert curated three-dimensional TCR and TCR-pMHC structures into a standardized, quantitative feature space that can be used for statistical analysis, mechanistic interpretation, and downstream machine learning.

In this phase, raw coordinate-level structural information is transformed into biologically interpretable descriptors that capture TCR architecture, CDR loop organization, antigen-contact geometry, and receptor orientation relative to the pMHC complex.

This phase is central to the project because it bridges structural biology and computational analysis: it defines how three-dimensional TCR conformations are operationalized as measurable variables.

---

### 5.2. Scientific Rationale

The T cell receptor is not only defined by its amino acid sequence, but also by its structural arrangement in complex with peptide-MHC. Differences in loop length, inter-chain orientation, docking geometry, and residue contact patterns may affect how TCRs recognize antigen and transmit activation signals.

Accordingly, this phase tests whether geometric properties of the TCR provide a meaningful structural representation of receptor behavior, especially in the context of anti-tumor immunity in colorectal cancer.

Rather than relying only on sequence-derived variables, this phase explicitly captures three-dimensional organization, which may reveal functional differences not visible from sequence alone.

---

### 5.3. Core Objectives

- define a reproducible set of geometric and structural TCR features;
- extract quantitative descriptors from QC-approved structural models;
- standardize feature definitions across all structures;
- generate a clean feature matrix suitable for downstream analysis;
- document all assumptions, approximations, and computational choices;
- preserve interpretability of all extracted variables.

---

### 5.4. Feature Design Principles

All extracted features should satisfy the following criteria:

- biologically interpretable;
- computationally reproducible;
- robust to minor structural noise;
- comparable across structures;
- explicitly defined in terms of residue ranges, atom selection, and geometric formula;
- compatible with both statistical and machine learning workflows.

Features that cannot be defined consistently across all structures should be excluded or flagged as optional exploratory variables.

---

### 5.5. Input Requirements

This phase depends on the following inputs:

- QC-approved TCR or TCR-pMHC structure files;
- standardized chain annotations;
- residue mapping for TCR alpha and beta chains;
- CDR region definitions, preferably based on a consistent annotation scheme;
- metadata describing species, MHC class, antigen type, and structure resolution;
- preprocessing outputs from earlier phases.

---

### 5.6. Output Requirements

The main outputs of this phase are:

- a structured feature table in tabular format;
- a data dictionary describing every feature;
- intermediate calculation logs;
- feature-level QC reports;
- a list of missing or excluded features per structure;
- reproducible code for feature extraction.
### 5.7. Feature Categories

#### 5.7.1. Chain-Level Structural Features

These features describe the global properties of TCR alpha and beta chains.

Examples include:

- TCR alpha chain length;
- TCR beta chain length;
- number of resolved residues in each chain;
- fraction of missing residues;
- chain-specific coordinate completeness;
- amino acid composition of variable regions;
- physicochemical composition of CDR regions.

These features provide a first-order structural profile and support normalization across structures.

#### 5.7.2. CDR Region Features

The complementarity-determining regions are the most antigen-sensitive parts of the TCR and are therefore a priority for structural quantification.

Potential features include:

- CDR1α length;
- CDR2α length;
- CDR3α length;
- CDR1β length;
- CDR2β length;
- CDR3β length;
- geometric span of each CDR loop;
- loop centroid coordinates;
- loop compactness or extension;
- intra-loop residue distances;
- relative orientation of CDR loops.

Where consistent annotation is available, CDR features should be extracted using the same numbering scheme across all structures.

#### 5.7.3. Inter-Chain Geometric Features

These features quantify how TCR alpha and beta chains are arranged relative to one another.

Examples include:

- distance between the alpha and beta chain centroids;
- distance between CDR3α and CDR3β centroids;
- angle between approximate alpha and beta chain axes;
- relative twist between the two variable domains;
- inter-chain spatial separation at selected reference points;
- chain asymmetry indices.

These descriptors may capture conformational differences that influence receptor flexibility and docking behavior.

#### 5.7.4. TCR-pMHC Docking Geometry

When the structure contains a complete TCR-pMHC complex, the relative orientation of the TCR on the pMHC surface should be quantified.

Potential features include:

- docking angle between TCR and pMHC;
- tilt angle;
- crossing angle;
- rotational orientation of the receptor above the peptide-binding groove;
- approach vector of the TCR variable domains;
- positional offsets relative to the MHC cleft;
- orientation of the CDR3 loops toward the peptide.

These variables are especially relevant for understanding how geometric arrangement may influence signaling and recognition specificity.

#### 5.7.5. Contact-Based Features

Contact features summarize the physical interaction interface between the TCR and its binding partners.

Potential features include:

- number of atomic contacts between TCR and peptide;
- number of atomic contacts between TCR and MHC;
- contacts contributed by CDR3α;
- contacts contributed by CDR3β;
- hydrogen bond counts, if reliably computable;
- salt bridge counts, if reliably computable;
- buried surface area, if software and structure quality permit;
- interface contact density.

Contact features can provide a more functional view of receptor geometry than distance-only measurements.

#### 5.7.6. Surface and Shape Features

If computationally feasible, additional surface-level descriptors may be derived.

Examples include:

- solvent-accessible surface area of selected regions;
- local curvature measures;
- pocket or cavity descriptors;
- shape complementarity metrics;
- surface exposure of key residues.

These variables may be included as exploratory features, provided they can be computed consistently.

#### 5.7.7. Sequence-Integrated Structural Features

Where appropriate, structural variables can be combined with local sequence information.

Examples include:

- residue identity at structurally important positions;
- charge distribution across CDR loops;
- hydrophobicity index of loop residues;
- aromatic content in the antigen-contact region;
- physicochemical polarity profiles.

These features should be clearly distinguished from purely structural features.

### 5.8. Methodological Workflow

#### 5.8.1. Structure Parsing

- load PDB or mmCIF files;
- identify chains corresponding to TCR alpha, TCR beta, MHC, and peptide;
- validate atom and residue numbering;
- detect missing coordinates and incomplete regions;
- store parsed structure objects in a standardized internal format.

#### 5.8.2. Region Annotation

- map residue ranges for variable domains and CDR loops;
- determine coordinates for each annotated region;
- define reference residues or anchors for geometric calculations;
- verify consistency across structures.

#### 5.8.3. Coordinate Extraction

- extract atomic coordinates for selected residues;
- define representative atoms, such as Cα atoms or side-chain centroids, depending on the feature;
- compute chain centroids, region centroids, and spatial axes;
- record any ambiguity in residue or atom availability.

#### 5.8.4. Feature Computation

- calculate geometric distances, angles, and orientation measures;
- compute contact-related descriptors where applicable;
- derive structural summary statistics for each region;
- generate feature values using a fixed and documented formula set.

#### 5.8.5. Feature Validation

- check for impossible or unstable values;
- identify features with excessive missingness;
- detect features with zero variance;
- flag calculations affected by incomplete structures;
- verify that all features are biologically interpretable.

#### 5.8.6. Feature Matrix Assembly

- assemble all valid features into a single table;
- assign each row to one structure;
- ensure that column names are standardized and descriptive;
- save the matrix in a machine-readable format;
- generate a feature dictionary for future reference.

### 5.9. Feature Naming Convention

To maintain clarity and prevent ambiguity, feature names should follow a consistent scheme.

Recommended format:
```text
[region]_[descriptor]_[metric]
### 5.10. Quality Control for Extracted Features

Each extracted feature should undergo quality assessment.

Minimum QC checks include:

- missing value rate;
- outlier detection;
- distribution inspection;
- consistency across related features;
- sensitivity to incomplete coordinates;
- reproducibility across reruns.

Features that fail QC should be:

- removed;
- redefined;
- replaced with a more robust alternative;
- or explicitly retained as exploratory-only variables.

### 5.11. Data Standards

All feature tables should include at least the following metadata fields:

- structure ID;
- chain assignments;
- species;
- MHC class;
- peptide identity, if available;
- antigen source;
- disease association;
- resolution;
- annotation source;
- extraction date;
- software version;
- feature version.

This metadata is essential for traceability and later subgroup analysis.

### 5.12. Reproducibility Requirements

To preserve reproducibility, the following must be documented:

- exact algorithm used for each feature;
- residue mapping rules;
- atom selection strategy;
- chain identification logic;
- cutoff values used in contact analysis;
- coordinate reference frame assumptions;
- random seeds, if any stochastic steps are used;
- software libraries and versions;
- code commit hash.

If a feature depends on a heuristic approximation, that approximation must be explicitly stated.

### 5.13. Exclusion Criteria for Features

A feature should be excluded from the final matrix if:

- it cannot be calculated consistently across most structures;
- it is highly sensitive to missing atoms or missing residues;
- it has no clear biological interpretation;
- it is redundant with another more stable feature;
- it has excessive missingness;
- it is unstable across small coordinate perturbations.

This prevents the feature matrix from becoming noisy or uninterpretable.

### 5.14. Recommended Deliverables

By the end of this phase, the following deliverables should exist:

- a finalized structural feature matrix;
- a feature definition document;
- a QC summary of extracted features;
- a reproducible extraction pipeline;
- a list of failed or excluded features;
- a versioned record of feature engineering decisions.

### 5.15. Phase Completion Criteria

This phase is considered complete when:

- all valid structures have been converted into quantitative feature representations;
- each feature has a clear biological and computational definition;
- the feature matrix is ready for statistical analysis;
- feature extraction is reproducible from raw inputs;
- missingness and limitations are documented;
- the final output is suitable for publication-grade analysis.

Recommended file destinations:
```text
data/processed/tcr_feature_matrix.csv
data/processed/tcr_feature_matrix.parquet
data/metadata/feature_dictionary.md
results/reports/feature_extraction_qc.md
src/geometry_features/

## Phase 6: Exploratory, Statistical, and Hypothesis-Testing Analysis

### Phase Goal
The primary objective of this phase is to perform a rigorous statistical evaluation of the structural features extracted in Phase 5. We aim to identify patterns, correlations, and significant differences that characterize TCR geometry in the context of colorectal cancer (CRC) and antigen recognition. This phase transforms "raw features" into "biological insights."

---

### Core Objectives
- Identify the statistical distribution of geometric variables (docking angles, distances, contact counts).
- Perform correlation analysis to detect redundancies and functional relationships between structural features.
- Execute hypothesis testing (e.g., T-tests, ANOVA, or non-parametric equivalents) to compare TCR groups (e.g., tumor-infiltrating vs. peripheral, or high-affinity vs. low-affinity).
- Visualize high-dimensional structural data using dimensionality reduction techniques.
- Establish baseline metrics for "normal" vs. "atypical" TCR geometries.

---

### Analytical Workflow

#### 6.1. Univariate Analysis and Data Profiling
- **Distribution Assessment:** Evaluate normality (Shapiro-Wilk test) for geometric features like docking angles and CDR lengths.
- **Outlier Detection:** Identify structural anomalies that might represent experimental artifacts in the PDB models.
- **Summary Statistics:** Calculate mean, median, variance, and confidence intervals for all key metrics.

#### 6.2. Bivariate and Correlation Analysis
- **Feature Correlation:** Use Spearman/Pearson correlation matrices to understand how features like "CDR3 length" correlate with "docking tilt angles."
- **Collinearity Check:** Identify highly redundant features to simplify the model for Phase 7.
- **Scatter Plot Matrix:** Visualize relationships between the most critical geometric parameters.

#### 6.3. Comparative Statistics (Hypothesis Testing)
- **Subgroup Comparisons:** Compare geometric features across different MHC alleles or different peptide types (e.g., neoantigens vs. self-antigens in CRC).
- **Significance Testing:** Apply p-value corrections (e.g., Benjamini-Hochberg) to account for multiple testing across many geometric features.
- **Effect Size Calculation:** Measure the magnitude of structural differences (Cohen’s d or Eta-squared) to ensure biological relevance beyond statistical significance.

#### 6.4. Dimensionality Reduction and Clustering
- **PCA (Principal Component Analysis):** Identify the "principal axes" of TCR structural variation.
- **t-SNE / UMAP:** Visualize the structural landscape of the TCR repertoire to see if CRC-specific TCRs cluster together based on geometry.
- **Unsupervised Clustering:** Use K-means or Hierarchical clustering to discover novel "structural archetypes" of TCRs.

---

### Visualization Deliverables
- **Correlation Heatmaps:** Showing the interdependence of geometric features.
- **Box-and-Whisker Plots:** For comparing distributions across biological groups.
- **Volcano Plots:** (If applicable) to highlight features with high effect size and statistical significance.
- **PCA/UMAP Plots:** Mapping the "Geometric Space" of the TCR.

---

### Success Criteria
- Completion of a comprehensive statistical report in `results/reports/statistical_analysis.md`.
- Identification of at least 3-5 "Key Geometric Signatures" that distinguish TCR subgroups.
- Validation that observed structural variations are not merely products of low resolution or data noise.
- Finalized set of "Validated Features" to be used as inputs for the Phase 7 modeling.

---

### Status
**Planned**
## Phase 7: Computational Modeling and Machine Learning

### Phase Goal

The goal of this phase is to determine whether quantitative structural and geometric features of the T cell receptor (TCR), extracted in previous phases, can be used to model, classify, or predict biologically meaningful functional patterns related to antigen recognition, receptor behavior, and potential anti-tumor immune activity in colorectal cancer (CRC).

This phase transforms the curated structural feature space into computational models that can identify informative patterns, estimate predictive power, and rank the relative importance of TCR geometric variables.

The emphasis of this phase is not only predictive performance, but also interpretability, robustness, and biological plausibility.

---

### Scientific Rationale

TCR recognition is a high-dimensional structural phenomenon. Individual features such as CDR3 length, chain orientation, centroid distances, docking angle, or contact density may each contribute partially to receptor function, but meaningful biological behavior is likely to emerge from multivariate combinations of these features.

Machine learning provides a framework for integrating such multidimensional structural descriptors and detecting non-obvious relationships between TCR geometry and functional annotations.

In this project, modeling is used as an analytical instrument to test whether the three-dimensional architecture of the TCR contains enough structured information to discriminate between biologically distinct receptor states or categories.

Importantly, this phase is designed with the understanding that structural datasets in immunology are often limited in size. Therefore, the modeling strategy must prioritize overfitting control, transparent validation, and interpretable outputs over unnecessarily complex algorithms.

---

### Core Objectives

- define biologically meaningful prediction or classification tasks;
- prepare a machine-learning-ready dataset from the validated feature matrix;
- evaluate multiple model families appropriate for small-to-moderate structural datasets;
- quantify model performance using reproducible validation frameworks;
- identify the most informative structural features contributing to model decisions;
- assess model stability, generalizability, and biological interpretability;
- generate computational evidence that can support or reject the central structural hypothesis.

---

### Modeling Strategy Overview

This phase should proceed in a staged and hypothesis-driven manner.

The recommended order is:

1. define prediction targets;
2. prepare and clean the modeling dataset;
3. split data using leakage-aware validation strategies;
4. establish simple baseline models;
5. train and compare interpretable and non-linear models;
6. evaluate feature importance and decision behavior;
7. assess uncertainty and robustness;
8. document limitations and prevent overinterpretation.

The primary goal is not to achieve the highest possible accuracy in isolation, but to produce reliable and biologically defensible computational findings.

---

### Candidate Modeling Tasks

The exact modeling objective depends on available annotations. Potential tasks include:

#### 7.1. Binary Classification
Examples:
- tumor-associated vs non-tumor-associated TCR structures;
- peptide-reactive vs non-reactive receptors;
- high-contact vs low-contact TCR-pMHC interfaces;
- structurally compact vs structurally extended receptor classes;
- receptors with putative strong vs weak signaling-associated geometry.

#### 7.2. Multiclass Classification
Examples:
- grouping TCRs by antigen class;
- grouping by MHC restriction class;
- grouping by structural archetype discovered in Phase 6 clustering;
- grouping by functional annotation categories, if available.

#### 7.3. Regression Modeling
Examples:
- prediction of docking angle from structural subfeatures;
- prediction of contact burden;
- prediction of a continuous activation proxy score;
- prediction of geometric composite indices.

#### 7.4. Representation Learning or Unsupervised Modeling
If labels are sparse or weak:
- clustering in latent feature space;
- manifold learning;
- autoencoder-based representation compression;
- similarity network construction among TCR geometries.

These approaches should be considered exploratory unless externally validated.

---

### Input Data for Modeling

The modeling dataset should be based on outputs from Phase 5 and filtered according to results from Phase 6.

Required inputs:

- validated structural feature matrix;
- feature metadata and definitions;
- labels or target variables;
- structure-level metadata for subgroup analysis;
- missingness profile;
- exclusion log;
- train/test split definitions;
- version-controlled preprocessing pipeline.

Each row should correspond to one structure or one unique TCR-pMHC complex, and each column should correspond to one validated modeling feature or metadata field.

---

### Dataset Preparation

Before model training, the following steps must be completed.

#### 7.5. Feature Filtering
- remove features with near-zero variance;
- remove or flag highly collinear variables;
- exclude features with excessive missingness;
- prioritize features with stable definitions across all structures;
- distinguish core features from exploratory features.

#### 7.6. Missing Data Handling
Possible strategies:
- complete-case analysis for highly reliable subsets;
- median or KNN imputation for limited missingness;
- explicit missingness indicators if biologically meaningful;
- sensitivity analysis comparing imputed vs non-imputed datasets.

Imputation methods must be fitted only on training folds to avoid data leakage.

#### 7.7. Scaling and Transformation
Depending on model family:
- standardization for linear models, SVMs, PCA-based workflows;
- optional log-transform for skewed variables;
- robust scaling when outliers are present;
- no unnecessary scaling for tree-based methods unless justified.

#### 7.8. Label Definition and Harmonization
- define labels using explicit biological criteria;
- avoid ambiguous class definitions;
- document source of all labels;
- record uncertainty in weakly supported annotations;
- ensure that labels do not indirectly encode leakage from derived features.

---

### Data Splitting and Validation Design

Because structural immunology datasets are often small, validation design is critical.

#### 7.9. Train/Test Strategy
Recommended options:
- stratified train/validation/test split for sufficiently large datasets;
- repeated stratified k-fold cross-validation for moderate datasets;
- nested cross-validation for hyperparameter optimization;
- leave-one-group-out validation if structures cluster by antigen, donor, or PDB family.

#### 7.10. Leakage Prevention
Potential leakage sources include:
- multiple related structures from the same antigen system;
- nearly identical TCRs split across train and test folds;
- preprocessing fitted on the full dataset;
- target-derived features accidentally included in predictors.

To reduce leakage:
- split by biological grouping variable where possible;
- perform preprocessing within cross-validation pipelines;
- audit similarity among structures before final splitting.

#### 7.11. Class Imbalance Management
If labels are imbalanced:
- use class-weighted loss functions;
- apply balanced sampling only within training folds;
- report precision-recall metrics in addition to accuracy;
- avoid synthetic oversampling unless carefully justified.

---

### Recommended Model Families

The modeling pipeline should compare several model classes with increasing complexity.

#### 7.12. Baseline Models
Baseline models are necessary to establish whether learned structure exists in the data.

Examples:
- majority-class classifier;
- random classifier;
- simple threshold-based rule model;
- logistic regression with a minimal feature set.

These provide a reference point for all later performance claims.

#### 7.13. Interpretable Linear Models
Examples:
- logistic regression;
- elastic net regularized logistic regression;
- linear discriminant analysis;
- ridge regression or lasso regression for continuous targets.

Strengths:
- transparent coefficients;
- easy interpretability;
- robust on small datasets;
- suitable for publication when paired with confidence intervals.

#### 7.14. Tree-Based Models
Examples:
- decision tree;
- random forest;
- gradient boosting;
- XGBoost or LightGBM, if dataset size permits.

Strengths:
- capture non-linear relationships;
- tolerate mixed feature behavior;
- provide feature importance estimates;
- often perform well on tabular biological data.

#### 7.15. Kernel-Based Models
Examples:
- support vector machine with linear or RBF kernel.

Strengths:
- useful for small to medium datasets;
- can model non-linear boundaries;
- may outperform more complex approaches when features are carefully scaled.

#### 7.16. Neural Network Models
Examples:
- shallow multilayer perceptron;
- small feed-forward neural networks.

These should be considered only if:
- dataset size is sufficient;
- regularization is strong;
- model complexity is tightly controlled.

Deep architectures are not recommended as default for small structural datasets unless the project later expands substantially.

---

### Hyperparameter Optimization

Hyperparameter tuning should be systematic and reproducible.

Recommended practices:
- use grid search or randomized search within cross-validation;
- tune only on training data;
- document parameter search spaces;
- avoid excessively wide searches on very small datasets;
- use nested cross-validation for unbiased performance estimation.

All selected hyperparameters must be recorded in the final modeling report.

---

### Performance Evaluation

Performance evaluation should be aligned with the modeling task.

#### 7.17. Classification Metrics
Recommended metrics:
- accuracy;
- balanced accuracy;
- precision;
- recall;
- F1-score;
- AUROC;
- AUPRC;
- confusion matrix.

Balanced accuracy and AUPRC are especially important in imbalanced datasets.

#### 7.18. Regression Metrics
Recommended metrics:
- mean absolute error;
- root mean squared error;
- R-squared;
- Spearman correlation between predicted and observed values.

#### 7.19. Stability and Uncertainty
In addition to average performance:
- report standard deviation across folds;
- compute confidence intervals where possible;
- examine calibration when probabilistic outputs are used;
- assess whether performance remains stable across resampling runs.

Single-split performance should never be the only reported result.

---

### Model Interpretation

Interpretability is a central requirement of this project.

#### 7.20. Global Feature Importance
Possible methods:
- model coefficients for linear models;
- impurity-based importance for tree models;
- permutation importance;
- SHAP values for selected final models.

#### 7.21. Local Explanation
For specific structures:
- evaluate which features drove a predicted class;
- inspect whether model decisions align with structural biology expectations;
- identify unusual cases where the model relies on unexpected variables.

#### 7.22. Biological Interpretation Layer
All important features must be mapped back to:
- specific TCR regions;
- docking behavior;
- contact topology;
- CDR loop architecture;
- known immunological mechanisms when possible.

A computationally important feature is not automatically biologically causal; interpretation must remain cautious.

---

### Robustness and Sensitivity Analysis

To avoid overclaiming, the following sensitivity analyses are recommended:

- repeat modeling after removing highly correlated features;
- repeat modeling on high-resolution structures only;
- compare performance using complete-case vs imputed datasets;
- test effect of excluding structurally ambiguous complexes;
- evaluate whether performance is dominated by one antigen class or one PDB family;
- compare core-feature-only models against full-feature models.

These analyses help determine whether findings are genuine or artifact-driven.

---

### Expected Deliverables

By the end of this phase, the following deliverables should be produced:

- a machine-learning-ready modeling dataset;
- a documented preprocessing pipeline;
- baseline and optimized model comparison tables;
- cross-validated performance reports;
- feature importance analyses;
- sensitivity analysis results;
- model interpretation figures;
- a methodological summary for manuscript integration.

Recommended output locations:
```text
data/modeling/model_input_table.csv
data/modeling/train_test_splits.json
results/models/model_comparison.csv
results/models/best_model_metrics.md
results/models/feature_importance.csv
results/figures/model_performance/
results/figures/feature_importance/
src/modeling/
## Phase 8: Biological Interpretation and CRC Relevance

### 8.1. Phase Goal

The goal of this phase is to interpret the extracted structural, geometric, statistical, and machine learning findings in a biologically meaningful context, with specific emphasis on colorectal cancer immune recognition.

This phase connects computational observations to immunological mechanisms, tumor antigen recognition, TCR-pMHC interaction biology, and potential implications for anti-tumor immunity.

Rather than treating structural features as abstract numerical variables, this phase evaluates whether observed patterns may reflect biologically relevant differences in TCR recognition, binding orientation, antigen engagement, or immune response behavior in colorectal cancer.

---

### 8.2. Scientific Rationale

Colorectal cancer is shaped by complex interactions between tumor cells, neoantigens, antigen presentation machinery, tumor-infiltrating lymphocytes, and immune escape mechanisms. TCRs are central to this process because they define how T cells recognize peptide-MHC complexes derived from tumor-associated or tumor-specific antigens.

Structural differences in TCR geometry may influence:

- how the receptor docks onto peptide-MHC;
- how CDR loops contact tumor-derived peptides;
- whether recognition is peptide-focused or MHC-focused;
- how stable or permissive a TCR-pMHC interaction may be;
- whether receptor geometry is compatible with productive immune signaling;
- how different TCRs may discriminate between self, tumor-associated, and neoantigenic peptides.

Therefore, linking TCR structural features to colorectal cancer biology can generate mechanistic hypotheses about anti-tumor recognition and immune surveillance.

---

### 8.3. Core Objectives

- interpret structural features in relation to known TCR recognition mechanisms;
- identify biologically meaningful geometric patterns;
- connect TCR-pMHC docking features to antigen recognition in CRC;
- evaluate whether statistical or ML-derived signals are immunologically plausible;
- distinguish robust biological signals from computational artifacts;
- generate testable mechanistic hypotheses;
- define limitations in biological interpretation.

---

### 8.4. CRC Immunobiology Context

#### 8.4.1. Tumor Antigens in Colorectal Cancer

Colorectal cancer may present multiple classes of antigens, including:

- neoantigens derived from somatic mutations;
- tumor-associated antigens;
- cancer-testis antigens;
- frameshift peptides, especially in microsatellite instability-high tumors;
- viral or microbiome-associated antigens in selected contexts;
- differentiation-associated antigens.

These antigen classes may differ in their immunogenicity, clonality, abundance, and likelihood of generating TCR-mediated recognition.

#### 8.4.2. Microsatellite Instability and TCR Recognition

Microsatellite instability-high CRC often exhibits increased mutational burden and frameshift-derived neoantigens. This may increase the probability of productive T cell recognition and shape the TCR repertoire.

Relevant interpretation points include:

- whether TCRs associated with MSI-high contexts show distinct CDR3 geometry;
- whether antigen-contact features are enriched in peptide-facing CDR loops;
- whether docking orientations suggest strong peptide engagement;
- whether structural patterns are compatible with neoantigen-driven selection.

#### 8.4.3. MHC Restriction and Antigen Presentation

TCR recognition is constrained by MHC presentation. Therefore, structural interpretation should consider:

- MHC class I versus class II context;
- HLA allele identity where available;
- peptide length and conformation;
- orientation of the peptide in the MHC groove;
- whether TCR contacts are peptide-dominant or MHC-dominant.

Differences in MHC restriction may explain variation in docking geometry and contact distributions.

---

### 8.5. Interpretation of Structural Feature Classes

#### 8.5.1. CDR Loop Geometry

CDR loops, particularly CDR3α and CDR3β, are central to antigen specificity.

Biological interpretation should examine whether:

- longer CDR3 loops show increased peptide contact potential;
- compact CDR loops correspond to constrained recognition modes;
- extended loops may penetrate deeper into the peptide-binding groove;
- CDR3α and CDR3β show asymmetric roles in peptide engagement;
- loop orientation differs between CRC-relevant and non-CRC-associated structures.

Potential biological implication:

- altered CDR geometry may reflect antigen-driven selection or adaptation to tumor-derived peptides.

#### 8.5.2. Inter-Chain Geometry

Inter-chain features describe how TCR alpha and beta variable domains are spatially arranged.

Interpretation should evaluate whether:

- alpha-beta centroid distance influences CDR loop positioning;
- variable-domain orientation affects the antigen-binding surface;
- altered chain geometry changes docking compatibility;
- inter-chain asymmetry modifies peptide versus MHC contact distribution.

Potential biological implication:

- global TCR architecture may constrain or enable specific recognition modes.

#### 8.5.3. Docking Geometry

Docking orientation determines how the TCR is positioned relative to the peptide-MHC surface.

Interpretation should consider:

- crossing angle;
- tilt angle;
- rotational orientation;
- positional offset over the MHC groove;
- directionality of CDR3 loops toward the peptide.

Potential biological implication:

- CRC-associated TCRs may use characteristic docking strategies when recognizing tumor-derived peptides.

#### 8.5.4. Contact-Based Features

Contact features are among the most directly interpretable structural descriptors.

Interpretation should examine:

- total TCR-peptide contact count;
- total TCR-MHC contact count;
- CDR3α-specific peptide contacts;
- CDR3β-specific peptide contacts;
- peptide-focused versus MHC-focused recognition;
- distribution of hydrogen bonds and salt bridges;
- contact density across the interface.

Potential biological implication:

- increased peptide-directed contacts may indicate recognition patterns more dependent on tumor antigen identity.

#### 8.5.5. Surface and Shape Features

Surface-level descriptors may reflect binding compatibility and interface complementarity.

Interpretation should consider:

- whether higher shape complementarity correlates with stronger interaction potential;
- whether surface exposure of key residues supports antigen engagement;
- whether local curvature or pocket-like regions influence peptide accommodation;
- whether surface properties differ across antigen classes.

Potential biological implication:

- surface geometry may contribute to selective recognition of specific CRC-derived peptide-MHC complexes.

---

### 8.6. Integration with Statistical Findings

Statistical findings should be interpreted according to effect size, uncertainty, and biological plausibility.

Key interpretation steps include:

- prioritize features with consistent directionality across analyses;
- evaluate confidence intervals rather than relying only on p-values;
- identify whether significant features map to biologically meaningful regions;
- compare statistical results with known TCR recognition principles;
- avoid overinterpreting features with high missingness or poor QC;
- separate exploratory observations from confirmatory conclusions.

Features should be considered biologically meaningful only if they are:

- statistically supported;
- structurally interpretable;
- robust to sensitivity analysis;
- consistent with known immunological mechanisms;
- not explained by obvious confounders such as resolution, chain completeness, or MHC class.

---

### 8.7. Integration with Machine Learning Findings

Machine learning results should be used primarily as hypothesis-generating evidence unless validated externally.

Interpretation should focus on:

- which features are repeatedly important across models;
- whether important features belong to biologically plausible categories;
- whether model explanations converge with statistical findings;
- whether prediction performance exceeds baseline expectations;
- whether learned patterns are stable across cross-validation splits;
- whether feature importance may be biased by correlated variables.

Recommended interpretability tools include:

- permutation importance;
- SHAP values;
- partial dependence analysis;
- feature stability analysis across folds;
- correlation-aware interpretation.

ML-derived signals should not be treated as mechanistic proof without biological validation.

---

### 8.8. Linking Findings to CRC Immune Phenotypes

Where metadata are available, structural findings may be interpreted in relation to CRC immune phenotypes.

Potential biological contexts include:

- MSI-high versus microsatellite-stable CRC;
- high versus low tumor mutational burden;
- immune-inflamed versus immune-excluded tumors;
- checkpoint inhibitor responsive versus resistant cases;
- neoantigen-rich versus neoantigen-poor tumors;
- CD8-dominant versus CD4-dominant T cell responses.

Possible interpretation questions:

- do TCRs associated with immunogenic CRC contexts show stronger peptide-focused geometry?
- are CDR3 features different in MSI-high-associated recognition?
- do docking orientations differ by antigen class?
- are contact features enriched in TCRs linked to anti-tumor responses?
- do certain geometric patterns suggest immune escape or weak antigen engagement?

---

### 8.9. Mechanistic Hypothesis Generation

This phase should produce testable hypotheses rather than unsupported conclusions.

Examples of possible hypotheses:

- CRC-associated TCRs recognizing neoantigens exhibit increased CDR3β-peptide contact density.
- MSI-high-associated TCR-pMHC complexes show more peptide-focused docking than MSS-associated complexes.
- Certain TCR alpha-beta inter-chain geometries favor recognition of frameshift-derived peptides.
- TCRs with extended CDR3 loops may better accommodate protruding tumor-derived peptides.
- Reduced peptide contact density may reflect weaker antigen discrimination or immune escape.
- Specific docking orientations may be associated with productive anti-tumor recognition.

Each hypothesis should be linked to:

- the feature(s) supporting it;
- the statistical or ML evidence;
- the biological rationale;
- the limitations and required validation.

---

### 8.10. Confounder-Aware Interpretation

Biological interpretation must account for possible confounders.

Important confounders include:

- structure resolution;
- missing residues or atoms;
- chain annotation errors;
- MHC class;
- HLA allele identity;
- peptide length;
- organism species;
- experimental method;
- redundancy among similar TCRs;
- publication or database bias;
- unequal representation of antigen classes.

Any biological conclusion should be checked against these variables when possible.

---

### 8.11. Literature Cross-Validation

Findings should be compared with existing literature on TCR recognition, tumor immunology, and colorectal cancer.

Literature validation should address:

- whether observed geometric patterns are consistent with known TCR-pMHC docking principles;
- whether CRC-associated antigens have known structural recognition modes;
- whether similar CDR3 or docking patterns have been reported in cancer immunology;
- whether findings align with known MSI-high immunogenicity;
- whether any result contradicts established mechanisms.

Contradictory findings should not be discarded automatically; they should be flagged as potential novel observations or artifacts requiring further validation.

---

### 8.12. Biological Interpretation Framework

Each major finding should be interpreted using a structured framework:
```text
Finding:
Observed structural/geometric pattern.

Evidence:
Statistical result, model output, or descriptive observation.

Biological interpretation:
Possible immunological meaning.

CRC relevance:
How the finding may relate to colorectal cancer biology.

Limitations:
Confounders, uncertainty, missing metadata, or model limitations.

Validation required:
Experimental, computational, or literature-based validation needed.
### 8.13. Expected Outputs

The outputs of this phase should include:

- a biological interpretation report;
- a table linking major features to possible immunological meanings;
- a list of prioritized mechanistic hypotheses;
- literature-supported interpretation notes;
- a confounder assessment summary;
- a distinction between supported findings and exploratory observations;
- candidate figures or diagrams for manuscript preparation.

Recommended file destinations:
```text
results/reports/biological_interpretation_crc.md
results/tables/feature_biological_interpretation.csv
results/tables/mechanistic_hypotheses.csv
results/reports/confounder_interpretation_summary.md
### 8.14. Phase Completion Criteria

This phase is considered complete when:

- major structural and computational findings have been interpreted biologically;
- CRC relevance has been explicitly discussed;
- statistical and ML results have been integrated into mechanistic reasoning;
- confounders and limitations have been documented;
- unsupported claims have been avoided;
- testable hypotheses have been generated;
- outputs are suitable for inclusion in a manuscript, thesis, or research report.

### 8.15. Status

**Planned**
