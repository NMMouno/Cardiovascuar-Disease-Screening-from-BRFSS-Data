# Cardiovascuar-Disease-Screening-from-BRFSS-Data
Trust-Aware Adaptive Mixture-of-Experts for Reliable Cardiovascular Disease Classification
Research implementation and supporting materials for a trustworthy machine learning framework using BRFSS cardiovascular health data.
Overview
This repository accompanies the research manuscript "Trust-Aware Adaptive Mixture-of-Experts for Reliable Cardiovascular Disease Classification", submitted to Measurement (Elsevier).
The study investigates how heterogeneous machine learning models can be combined through reliability-informed adaptive gating to improve cardiovascular disease-status classification. Beyond conventional predictive discrimination, the framework evaluates multiple aspects of trustworthy AI, including calibration, uncertainty estimation, selective prediction, fairness, and robustness.
The prediction task concerns existing, self-reported cardiovascular disease status, rather than future cardiovascular event prediction.
Key Contributions
•	Trust-aware adaptive Mixture-of-Experts: Combines heterogeneous predictive models using sample-specific gating informed by expert predictions, disagreement, entropy, confidence, and selected clinical characteristics.
•	Diversity-aware expert selection: Integrates complementary tree-based, neural, and linear predictors.
•	Probability calibration: Evaluates the reliability of probabilistic predictions using Brier score, negative log-likelihood, and expected calibration error.
•	Uncertainty-guided selective prediction: Identifies uncertain observations that may benefit from additional human review.
•	Localized false-negative recovery: Investigates targeted decision refinement for borderline observations.
•	Fairness assessment: Examines prediction disparities across sex, age, education, and income groups.
•	Input robustness: Evaluates sensitivity to Gaussian noise, feature masking, and binary feature flipping.
•	Cross-dataset evaluation: Investigates predictive transfer between BRFSS 2015 and BRFSS 2020 using harmonized predictors.
Datasets
BRFSS 2015 — Primary Dataset
The primary dataset contains 253,680 observations, with 21 predictive attributes and the binary target HeartDiseaseorAttack.
Property	Value
Observations	253,680
Predictive features	21
Positive observations	23,893
Positive prevalence	9.42%
Development partition	202,944
Independent holdout partition	50,736
The predictors include demographic, behavioral, and self-reported health indicators.
BRFSS 2020 — Cross-Dataset Evaluation
The external dataset contains 319,795 observations, with approximately 8.56% positive prevalence.
Because the datasets have different feature representations, 12 predictors were harmonized for the cross-dataset experiment. A separate feature-restricted model was developed on BRFSS 2015 and evaluated on BRFSS 2020 without external retraining or recalibration.
The external experiment is distinct from the main 21-feature evaluation. Differences in outcome definitions and survey processing should be considered when interpreting the results.
Proposed Framework
The framework integrates five heterogeneous predictive experts:
1.	CatBoost
2.	MLP with robustness-oriented FGSM training
3.	Focal-loss MLP
4.	AutoInt
5.	Logistic Regression with selected predictors
Each expert generates probability estimates, which are combined using a sample-specific gating mechanism informed by reliability-related meta-features.
The framework also evaluates uncertainty-guided decision policies, fairness-aware threshold adjustments, and model performance under imperfect inputs.
Main Experimental Results
The following results are reported in the accompanying manuscript for the independent BRFSS 2015 holdout evaluation.
Metric	Result
PR-AUC	0.3820
ROC-AUC	0.8610
Precision	0.3448
Recall	0.5652
F1-score	0.4283
Brier Score	0.0695
Negative Log-Likelihood	0.2348
Expected Calibration Error	0.0030
Uncertainty-Guided Selective Prediction
Under the evaluated uncertainty threshold:
•	Automated coverage: 93.2%
•	Deferred observations: 6.8%
•	Proportion of observed classification errors contained within the deferred subset: approximately 45%
These results describe error concentration under the evaluated selective prediction policy. They do not establish that deferred errors were corrected by clinicians.
Cross-Dataset Evaluation
Evaluation cohort	PR-AUC	ROC-AUC
BRFSS 2015 holdout, 12 features	0.3564	0.8373
BRFSS 2020 external, 12 features	0.3391	0.8406
The results demonstrate predictive transfer under a shared feature representation, while differences between the curated datasets limit conclusions about clinical transportability.
Repository Contents and Reproducibility
This repository provides research code and supporting materials associated with the BRFSS-based cardiovascular disease classification study.
The manuscript documents the model architecture, evaluation protocol, performance measures, and limitations of the experiments. The availability of individual scripts, generated artifacts, and complete end-to-end reproduction steps should be determined from the files included in this repository.
The reported results should not be interpreted as independently reproduced merely because they appear in this README.
Research Limitations
The study has several important limitations:
•	The target represents self-reported existing cardiovascular disease, not prospective disease incidence.
•	The dataset does not include detailed clinical measurements or longitudinal follow-up.
•	The reported uncertainty weighting was not validated through a complete normalization sensitivity study.
•	Calibration after localized decision-score adjustment was not independently established.
•	Fully nested expert selection and isotonic-calibration cross-fitting were not completely verified.
•	Input-corruption tests do not establish robustness against clinically constrained adversarial attacks.
•	The external evaluation uses a separate 12-feature model rather than directly transferring the original 21-feature system.
The framework is intended for methodological research and evaluation, not as a clinically validated diagnostic system.
Publication
Manuscript: Trust-Aware Adaptive Mixture-of-Experts for Reliable Cardiovascular Disease Classification
Authors: Nasirul Mumenin, Tahmid Hasan, Muhammad Mostafa Monowar, Md Abdul Hamid
Journal: Measurement (Elsevier)
Manuscript status: Under review / revision.
Citation
If you use this research or its accompanying materials, please cite the associated manuscript once its final bibliographic details are available.
Contact
For research questions and collaboration:
Nasirul Mumenin
Department of Computer Science and Engineering
Bangladesh University of Business and Technology (BUBT), Bangladesh
Disclaimer
This repository is intended for academic research and educational purposes. Its outputs should not be used for clinical diagnosis, treatment decisions, or deployment without appropriate independent validation and regulatory assessment.

