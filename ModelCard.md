# Model Card

## Model name

**mtDNA Dual-Reporter Programmability Simulator**

## Model version

Version 1.0

## Model type

This is a **mechanistically informed simulation and analysis framework** that combines:

- synthetic biological data generation
- rule-based serial barrier modeling
- supervised machine learning
- feature-importance analysis
- visualization of design space

It is not a single predictive model only. It is a pipeline that produces synthetic datasets and then trains multiple predictive models on those datasets.

## Summary

The framework models mitochondrial programmability for an engineered **mtDNA-like nucleic acid cargo** carrying **mtNanoLuc** and **sfGFP**.

The model assumes that successful mitochondrial programming depends on sequential passage through several stages:

- cell entry
- intracellular trafficking
- mitochondrial docking
- membrane and matrix access
- matrix retention
- target engagement
- downstream functional rescue

The overall score, `Phi_prog`, is computed as a product of step-specific probabilities. Downstream reporter outputs and mitochondrial-function variables are then generated.

## Intended users

This framework is intended for:

- computational biologists
- mitochondrial biologists
- synthetic biologists
- drug-delivery researchers
- students learning systems modeling
- researchers exploring organelle engineering design spaces

## Intended use

Appropriate uses include:

- exploring which features may influence mitochondrial cargo success
- ranking hypothetical delivery designs
- studying serial biological bottlenecks
- generating synthetic benchmark datasets
- supporting conceptual manuscript development
- planning future experimental studies

## Out-of-scope use

This framework should not be used for:

- clinical diagnosis
- patient stratification
- treatment selection
- regulatory submission as experimental evidence
- claims of validated mitochondrial gene delivery in humans
- claims that mtNanoLuc-sfGFP mtDNA expression has been established experimentally in the exact form modeled here

## Inputs

The model uses simulated or derived values for features such as:

- payload size
- engineered insert size
- negative charge density
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
- mitochondrial membrane potential
- ATP availability
- TOM/TIM competence
- PAM activity
- nucleoid access
- baseline ROS
- baseline OCR

## Outputs

The framework produces:

### Intermediate outputs
- `P_cell`
- `P_traffic`
- `P_dock`
- `P_transloc`
- `P_retain`
- `P_engage`
- `Phi_prog`

### Reporter outputs
- `mtNanoLuc_signal`
- `sfGFP_signal`

### Functional outputs
- `ATP_post`
- `OCR_post`
- `ROS_post`
- `Psi_m_abs_post`
- `G_func`

### Labels
- `successful_programming`
- `strong_rescue`

## Training and evaluation

After simulation, the pipeline trains machine learning models for:

### Classification
To predict:
- `successful_programming`

Models used:
- Logistic Regression
- Random Forest Classifier
- Gradient Boosting Classifier

Metrics:
- ROC-AUC
- PR-AUC
- Accuracy
- F1 score

### Regression
To predict:
- `G_func`

Models used:
- Ridge Regression
- Random Forest Regressor
- Gradient Boosting Regressor

Metrics:
- RMSE
- R²

## Performance summary

In the current synthetic run:

- successful programming rate was low
- strong rescue events were rare
- classification performance was strong
- regression performance was weak

This suggests that the simulator currently defines a clearer binary success boundary than a smooth continuous rescue landscape.

## Model assumptions

The framework assumes:

1. Mitochondrial programming is a serial multi-step process.
2. Failure at one major step can strongly reduce final success.
3. Membrane potential, ATP, import competence, and targeting chemistry influence access.
4. Large nucleic-acid payloads face stronger transport penalties than small molecules.
5. Reporter output depends on both delivery success and expression compatibility.
6. Functional rescue depends on both reporter-associated success and mitochondrial-state variables.

## Limitations

### Synthetic nature
All training and evaluation data are simulated.

### Mechanistic simplification
The framework uses biologically motivated abstractions for mitochondrial access and expression. These abstractions are not direct measurements of all real mitochondrial processes.

### Cargo-specific uncertainty
The exact dual-reporter mtDNA-like construct is hypothetical in this framework.

### Generalization limitation
Because the model is trained on synthetic data, strong performance on the synthetic classification task does not imply strong real-world predictive power.

## Bias and risk considerations

Potential risks include:

- overinterpreting synthetic results as experimental fact
- assuming feature importance directly reflects real biological causality
- using the model outside its intended research-exploration context
- treating simulated expression compatibility as proof of real mitochondrial gene expression feasibility

## Ethical considerations

This repository is meant for computational exploration and should be used transparently. Any downstream claims should clearly state that the current framework is synthetic and hypothesis-generating.

## Maintenance

This model card should be updated when:

- feature definitions change
- equations are recalibrated
- new datasets are introduced
- experimental data are incorporated
- evaluation strategy is changed

## Contact

**Mark I.R. Petalcorin**  
Add preferred contact information here.
