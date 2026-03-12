# mtDNA Dual-Reporter Programmability Simulator

A mechanistically informed in silico framework for modeling mitochondrial programmability of an engineered **mtDNA-like nucleic acid cargo** carrying **mtNanoLuc** and **sfGFP** reporter modules.

## Overview

This project simulates mitochondrial delivery and function as a **serial control problem**. The central idea is that a large nucleic acid cargo must pass through several barriers in sequence before it can produce a useful mitochondrial outcome.

The modeled stages are:

1. **Cell entry**
2. **Intracellular trafficking**
3. **Mitochondrial docking**
4. **Membrane and matrix access**
5. **Matrix retention**
6. **Target engagement**
7. **Functional rescue**

The simulator generates synthetic datasets and applies machine learning to identify which design and biological features most strongly influence successful mitochondrial programming.

## Biological focus

This version of the framework is focused specifically on a hypothetical engineered **mtDNA-like payload** carrying two reporter modules:

- **mtNanoLuc**
- **sfGFP**

The model includes features relevant to both delivery and expression, including:

- payload size
- engineered insert size
- nucleic-acid charge burden
- compactness
- TPP-like targeting fraction
- MTS-like targeting fraction
- fusogenicity
- endosomal escape
- nuclease resistance
- matrix binding
- clearance rate
- codon compatibility for mtNanoLuc
- codon compatibility for sfGFP
- promoter compatibility
- UTR compatibility
- bicistronic burden
- replication compatibility

## Key outputs

The workflow produces:

- a **main synthetic dataset**
- a **longitudinal synthetic dataset**
- classification results for **successful mitochondrial programming**
- regression results for **continuous functional rescue**
- feature-importance tables
- mechanistic plots
- PCA visualization
- summary report files

## Repository structure

```text
.
├── mtdna_mtnanoluc_sfgfp_programmability.py
├── mtdna_mtnanoluc_sfgfp_programmability_notebook.ipynb
├── simulated_mtdna_mtnanoluc_sfgfp_dataset.csv
├── simulated_mtdna_mtnanoluc_sfgfp_longitudinal.csv
├── mtdna_dual_reporter_classification_results.csv
├── mtdna_dual_reporter_classifier_importance.csv
├── mtdna_dual_reporter_regression_results.csv
├── mtdna_dual_reporter_regression_importance.csv
├── mtdna_dual_reporter_report.csv
├── mtdna_dual_reporter_barriers.png
├── mtdna_dual_reporter_classifier_performance.png
├── mtdna_dual_reporter_mechanistic_checks.png
├── mtdna_dual_reporter_longitudinal.png
├── mtdna_dual_reporter_pca.png
├── mtdna_dual_reporter_regression_fit.png
├── README.md
├── ModelCard.md
└── DataSheet.md
```

## How the simulator works

Each virtual sample is assigned:

- a **cell state**
- a **delivery mode**
- a **target mode**
- a set of **cargo design features**
- a set of **mitochondrial-state variables**

The code then computes the following barrier probabilities:

- `P_cell`
- `P_traffic`
- `P_dock`
- `P_transloc`
- `P_retain`
- `P_engage`

These are multiplied together to generate:

- `Phi_prog`, the overall mitochondrial programmability score

Reporter outputs are then simulated:

- `mtNanoLuc_signal`
- `sfGFP_signal`

Finally, downstream mitochondrial outcomes are estimated:

- `ATP_post`
- `OCR_post`
- `ROS_post`
- `Psi_m_abs_post`
- `G_func`

## Main tasks

### 1. Simulation
Generate synthetic mitochondrial programming experiments for thousands of virtual designs.

### 2. Classification
Predict whether a design achieves **successful programming**.

### 3. Regression
Predict the continuous **functional rescue score**.

### 4. Interpretation
Use feature-importance analysis to identify the strongest determinants of success.

## Intended use

This repository is designed for:

- hypothesis generation
- computational design ranking
- exploratory mitochondrial engineering analysis
- teaching and demonstration of serial biological control problems
- planning future wet-lab studies

## Not intended for

This repository is **not** intended to serve as:

- experimental proof of mitochondrial transfection
- clinical prediction
- direct therapeutic decision support
- evidence that a dual mtNanoLuc-sfGFP mtDNA construct is already validated in human mitochondria

## Installation

Create a Python environment with the required packages:

```bash
pip install numpy pandas matplotlib scikit-learn
```

## Usage

Run the Python script:

```bash
python mtdna_mtnanoluc_sfgfp_programmability.py
```

Or open the notebook:

```bash
jupyter notebook mtdna_mtnanoluc_sfgfp_programmability_notebook.ipynb
```

## Example outputs

The script generates:

- synthetic datasets in CSV format
- evaluation tables
- publication-style figures
- summary performance report

## Interpreting the results

A high `Phi_prog` suggests that the cargo is more likely to pass the sequential mitochondrial barriers successfully.

A high `G_func` suggests that the cargo is more likely to produce a useful downstream mitochondrial effect.

A design may score well in one part of the pipeline and still fail overall if another barrier is weak. This is a central feature of the serial-control logic.

## Limitations

This is a **synthetic, mechanistically informed simulator**. It does not prove that the modeled mtDNA-like dual-reporter system is experimentally validated in human mitochondria. All outputs should be interpreted as computational hypotheses.

## Citation

If you use this repository, please cite it as:

```text
Petalcorin, M. I. R. mtDNA Dual-Reporter Programmability Simulator. GitHub repository.
```

## License

Add your preferred license here, for example:

- MIT License
- Apache 2.0
- BSD 3-Clause

## Contact

**Mark I.R. Petalcorin**  
Add email, ORCID, GitHub, or institutional affiliation here.
