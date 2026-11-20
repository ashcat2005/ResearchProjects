# Undergraduate Thesis Proposal

## 1. Title
**Automated Radio Pulsar Candidate Classification Using Deep Learning and Multi-Modal Diagnostic Profiles**

---

## 2. Scope
Modern large-scale blind radio pulsar surveys—such as the High Time Resolution Universe (**HTRU**) survey, the **FAST** Commensal Radio Astronomy Survey (CRAFTS), and upcoming **Square Kilometre Array (SKA)** campaigns—generate tens of millions of candidate signals per observing run after searching across wide ranges of dispersion measures ($\text{DM}$) and trial spin periods ($P$). However, over $99.9\%$ of these detections are false positives caused by terrestrial Radio Frequency Interference (**RFI**), receiver thermal noise fluctuations, or harmonic aliases of bright known pulsars. Because manual visual inspection of diagnostic plots by human experts is no longer feasible at modern data rates, automated machine learning pipelines are essential for rapid, high-recall pulsar discovery.

A standard folded pulsar candidate is characterized by both summary statistical features (mean, standard deviation, excess kurtosis, and skewness of the folded pulse profile and $\text{DM}\text{--}\text{SNR}$ curve) and multi-dimensional diagnostic data arrays:
1. **Integrated Pulse Profile ($1\text{D}$):** Phase-folded flux intensity across rotational phase $\phi \in [0, 1)$, where genuine pulsars exhibit sharp, localized emission peaks.
2. **Dispersion Measure–Signal-to-Noise Curve ($\text{DM}\text{--}\text{SNR}$, $1\text{D}$):** Detection significance as a function of trial dispersion measure $\text{DM} = \int_0^d n_e\,dl$, peaking sharply at a non-zero astrophysical $\text{DM}$ rather than $\text{DM} = 0\text{ pc cm}^{-3}$ (terrestrial RFI).
3. **Time-vs.-Phase and Frequency-vs.-Phase Sub-Integration Plots ($2\text{D}$):** Persistence of the pulsed signal across observing sub-integrations and radio frequency channels.

This undergraduate thesis focuses on **designing, training, and benchmarking classical machine learning and deep neural network architectures in TensorFlow to separate genuine radio pulsars from RFI using public survey datasets**. The scope encompasses three progressive stages:
1. **Tabular Feature Engineering & Classical Baselines:** Utilizing the public **HTRU2** benchmark dataset ($17,898$ candidates, including $1,639$ confirmed real pulsars; Lyon et al. 2016) to address severe class imbalance ($\sim 9:1$ RFI-to-pulsar ratio) and establish baseline classifiers (Logistic Regression, Support Vector Machines, and Random Forests / Gradient Boosted Trees).
2. **1D Convolutional Neural Networks (CNNs) & Multi-Input Architectures:** Extending classification to raw diagnostic profile arrays (using public candidate datasets such as **HTRU-S LowLat** / **FAST** / **PICS** benchmark archives containing 1D pulse profiles, 1D $\text{DM}\text{--}\text{SNR}$ curves, and 2D time/frequency sub-bands) via multi-branch 1D/2D Convolutional Neural Networks implemented in `TensorFlow 2.x`.
3. **Interpretability, Threshold Calibration & Selection-Bias Analysis:** Applying Gradient-weighted Class Activation Mapping (**Grad-CAM**) and SHAP feature attribution to verify that the networks learn astrophysical signatures (non-zero $\text{DM}$ peaks and narrow duty cycles), and evaluating recall as a function of pulsar spin period $P$, pulse width, and signal-to-noise ratio ($\text{SNR}$).

Raw telescope baseband voltage recording, real-time FPGA/GPU dedispersion and Fourier-domain acceleration search pipelines, and single-pulse Fast Radio Burst (FRB) transient search triggers lie outside the scope of this project.

---

## 3. Objectives

### General Objective
To develop, validate, and benchmark a multi-modal deep learning classification framework in TensorFlow for automated radio pulsar candidate vetting, quantifying improvements in recall, precision, and interpretability over traditional feature-based machine learning models.

### Specific Objectives
1. **Exploratory Data Analysis & Class-Imbalance Pipeline:** Ingest the public **HTRU2** tabular dataset and raw multi-dimensional candidate archives (1D pulse profiles, 1D $\text{DM}\text{--}\text{SNR}$ curves, and 2D sub-integration arrays), implementing stratified train/validation/test splits, phase-alignment normalization (circularly shifting pulse peaks to phase $\phi = 0.5$), and class-imbalance mitigation strategies (focal loss, class weighting, and SMOTE).
2. **Classical Machine Learning Benchmarking:** Train and hyperparameter-tune baseline tabular classifiers (Random Forests, XGBoost, and RBF-kernel Support Vector Machines) on the 8 HTRU2 statistical features, establishing rigorous benchmark metrics ($F_1$-score, Precision–Recall AUC, and Recall at $1\%$ False Positive Rate).
3. **Multi-Branch Deep Neural Network Design:** Construct a multi-input Convolutional Neural Network in `TensorFlow 2.x` combining dedicated 1D convolutional branches for the integrated pulse profile and $\text{DM}\text{--}\text{SNR}$ curve with a 2D convolutional branch for time/frequency sub-integration plots, fusing learned representations into a calibrated probabilistic output.
4. **Domain-Specific Data Augmentation:** Implement astrophysically consistent data augmentation—including circular phase shifts, additive Gaussian thermal noise injection, and small $\text{DM}$-offset perturbations—to prevent overfitting on minority pulsar classes and improve generalization to faint, low-$\text{SNR}$ candidates.
5. **Model Explainability & Astrophysical Error Analysis:** Apply SHAP (for tabular models) and Grad-CAM / saliency maps (for CNN branches) to audit decision boundaries, and categorize misclassified pulsars by spin period ($P < 10\text{ ms}$ millisecond pulsars vs. long-period pulsars), duty cycle, and $\text{DM}$ to identify systematic astrophysical blind spots.

---

## 4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. **Open-Source Software Package (`pyPulsarNet`):**
   * A clean, modular, PEP-8 compliant Python package built on `TensorFlow 2.x`, `scikit-learn`, `NumPy`, `SciPy`, `Pandas`, `SHAP`, and `Matplotlib`.
   * Modules for automated HTRU2 and raw diagnostic array preprocessing, circular phase-centering, astrophysically motivated data augmentation, classical ML baselines, and multi-input 1D/2D CNN architectures.
   * Automated unit tests verifying tensor shapes, circular-shift invariance, focal-loss gradient flow, and probability calibration, paired with reproducible Jupyter notebooks generating all thesis figures.

2. **Scientific Visualization & Data Suite:**
   * Exploratory statistical distributions comparing real pulsars vs. RFI across skewness, excess kurtosis, and $\text{DM}\text{--}\text{SNR}$ metrics.
   * Precision–Recall (PR) curves, Receiver Operating Characteristic (ROC) curves, and normalized confusion matrices comparing Random Forests, Gradient Boosted Trees, and Multi-Input CNNs across varying false-positive-rate budgets.
   * Saliency and Grad-CAM diagnostic overlays on representative true-positive pulsars, false-positive RFI harmonics, and missed faint millisecond pulsars, alongside recall-vs.-$\text{SNR}$ and recall-vs.-spin-period completeness curves.

3. **Undergraduate Thesis Manuscript & Defense:**
   * A formal LaTeX-typeset undergraduate thesis (40–60 pages) covering radio pulsar search fundamentals, dispersion and RFI physics, machine learning and convolutional neural network methodology, quantitative model benchmarks, and astrophysical error analysis.
   * A 20-minute oral defense presentation summarizing the observational problem, deep learning architecture, empirical benchmarks, and conclusions.

---

## 5. 4 Months Timeline

The project is organized across **16 weeks (4 months)** into four structured monthly phases with concrete weekly milestones:

### Month 1: Pulsar Search Physics, Data Ingestion & Classical Baselines
* **Week 1:** Literature review of radio pulsar searching, interstellar dispersion, RFI morphology, and automated candidate classification (Lorimer & Kramer 2004; Eatough et al. 2010; Bates et al. 2012; Lyon et al. 2016; Zhu et al. 2014).
* **Week 2:** Set up the Python machine learning stack (`TensorFlow 2.x`, `scikit-learn`, `pandas`, `shap`) and download the public **HTRU2** dataset (UCI / Zenodo) alongside open multi-dimensional candidate diagnostic archives (**PICS** / **HTRU-S LowLat** public datasets).
* **Week 3:** Perform exploratory data analysis (EDA) on HTRU2 features, visualizing class separability, feature correlations, and the $9:1$ class-imbalance structure; establish leak-free stratified $k$-fold cross-validation splits.
* **Week 4:** Implement preprocessing routines for raw diagnostic plots (min-max normalization, circular phase shifting to center the pulse peak at $\phi = 0.5$, and bilinear resizing of 2D sub-integration arrays) and train classical baseline classifiers (Random Forest, SVM, Gradient Boosting).

### Month 2: Deep Learning Architecture & Class-Imbalance Optimization
* **Week 5:** Design and implement standalone 1D CNN classifiers in `TensorFlow 2.x` for the integrated pulse profile and $\text{DM}\text{--}\text{SNR}$ curve, evaluating kernel sizes, batch normalization, and global average pooling.
* **Week 6:** Implement the 2D CNN branch for time-vs.-phase and frequency-vs.-phase sub-integration plots, combining all branches into a unified multi-input neural network architecture (`tf.keras.Model`).
* **Week 7:** Address class imbalance and faint-signal generalization by implementing binary focal loss (Lin et al. 2017), class-weighted cross-entropy, and astrophysical data augmentation (phase jitter, synthetic thermal noise injection, and $\text{DM}$-curve scaling).
* **Week 8:** Conduct systematic hyperparameter tuning (learning rate schedules, dropout rates, and convolutional filter depths) using validation Precision–Recall AUC as the primary selection metric.

### Month 3: Benchmarking, Calibration & Model Interpretability
* **Week 9:** Evaluate all trained models (Random Forest, XGBoost, 1D CNN, and Multi-Input CNN) on the held-out test set, computing Precision–Recall AUC, $F_1$-score, Matthews Correlation Coefficient (MCC), and pulsar recall at strict false-positive thresholds ($\text{FPR} \le 0.5\%$ and $1\%$).
* **Week 10:** Perform probability calibration analysis (reliability diagrams and Brier score evaluation via Platt scaling / temperature scaling) so network outputs represent true posterior pulsar probabilities.
* **Week 11:** Implement model interpretability diagnostics using SHAP values for tabular features and Grad-CAM activation maps for the 1D/2D CNN branches, confirming that predictions rely on non-zero $\text{DM}$ peaks and broadband sub-band persistence.
* **Week 12:** Conduct an astrophysical error audit of false negatives (missed real pulsars) and false positives (misclassified RFI), mapping detection completeness across spin period ($P$), pulse duty cycle ($W_{50}/P$), dispersion measure ($\text{DM}$), and folded $\text{SNR}$.

### Month 4: Synthesis, Visualization & Thesis Writing
* **Week 13:** Benchmark inference throughput (candidates classified per second on CPU/GPU) to demonstrate scalability for next-generation survey pipelines (FAST / SKA data rates).
* **Week 14:** Generate publication-grade thesis figures (multi-branch CNN architecture schematic, Precision–Recall curves, confusion matrices, Grad-CAM diagnostic overlays, and completeness heatmaps). Draft Chapters 1–3 of the thesis (Introduction, Pulsar Search & RFI Physics, Deep Learning Methodology).
* **Week 15:** Draft Chapters 4–5 (Benchmarking Results, Model Interpretability, Astrophysical Error Analysis, and Conclusions). Clean, document, and finalize the `pyPulsarNet` GitHub repository.
* **Week 16:** Advisor review, feedback integration, LaTeX typesetting polish, final thesis submission, and rehearsal of the 20-minute defense presentation.

---

## 6. References

1. **Lorimer, D. R., & Kramer, M.** (2004). *Handbook of Pulsar Astronomy*. Cambridge University Press.
2. **Eatough, R. P., Molkenthin, N., Kramer, M., Noutsos, A., Keith, M. J., Stappers, B. W., & Lyne, A. G.** (2010). *Selection of radio pulsar candidates using artificial neural networks*. Monthly Notices of the Royal Astronomical Society, 407(4), 2443–2450.
3. **Bates, S. D., et al.** (2012). *The High Time Resolution Universe Pulsar Survey – VI. An artificial neural network and timing of 75 pulsars*. Monthly Notices of the Royal Astronomical Society, 427(2), 1052–1065.
4. **Zhu, W. W., et al.** (2014). *Searching for Pulsars Using Image Pattern Recognition*. The Astrophysical Journal, 781(2), 117.
5. **Morello, V., Barr, E. D., Bailes, M., Flynn, C. M., Keane, E. F., & van Straten, W.** (2014). *SPINN: a straightforward machine learning solution to the pulsar candidate selection problem*. Monthly Notices of the Royal Astronomical Society, 443(2), 1651–1662.
6. **Lyon, R. J., Stappers, B. W., Cooper, S., Brooke, J. M., & Knowles, J. D.** (2016). *Fifty years of pulsar candidate selection: from simple filters to a new principled real-time classification approach*. Monthly Notices of the Royal Astronomical Society, 459(1), 1104–1123.
7. **Lin, T.-Y., Goyal, P., Girshick, R., He, K., & Dollár, P.** (2017). *Focal Loss for Dense Object Detection*. Proceedings of the IEEE International Conference on Computer Vision (ICCV), 2980–2988.
8. **Selvaraju, R. R., Cogswell, M., Das, A., Vedantam, R., Parikh, D., & Batra, D.** (2017). *Grad-CAM: Visual Explanations from Deep Networks via Gradient-Based Localization*. Proceedings of the IEEE International Conference on Computer Vision (ICCV), 618–626.
9. **Bethapudi, S., & Desai, S.** (2018). *Separation of pulsar signals from noise using supervised machine learning algorithms*. Astronomy and Computing, 23, 15–26.
10. **Guo, P., et al.** (2019). *Pulsar candidate classification using generative adversarial networks*. Monthly Notices of the Royal Astronomical Society, 490(4), 5424–5439.
11. **Wang, H., et al.** (2019). *Pulsar candidate selection using ensemble networks for FAST drift-scan survey*. Science China Physics, Mechanics & Astronomy, 62(5), 959507.
12. **Balakrishnan, V., Champion, D., Barr, E., Kramer, M., Sengar, R., & Bailes, M.** (2021). *Pulsar candidate identification using semi-supervised generative adversarial networks*. Monthly Notices of the Royal Astronomical Society, 505(1), 1180–1194.