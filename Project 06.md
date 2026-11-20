# Undergraduate Thesis Proposal

## 1. Title
**Population Synthesis, Magnetic Braking, and Evolutionary Tracks on the Pulsar $P\text{--}\dot{P}$ Diagram**

---

## 2. Scope
Rotation-powered pulsars act as cosmic flywheels whose rotational kinetic energy is steadily converted into electromagnetic radiation and relativistic particle winds. Measuring a pulsar's spin period $P$ and its first time derivative $\dot{P} = dP/dt$ via high-precision radio, X-ray, or $\gamma$-ray timing places every known neutron star on the diagnostic **$P\text{--}\dot{P}$ diagram**—the neutron star equivalent of the Hertzsprung–Russell diagram. Within the classical vacuum magnetic dipole braking framework, these two observables yield immediate estimates of the spin-down luminosity $\dot{E}$, surface dipolar magnetic field strength $B_s$, and characteristic age $\tau_c$:

$$\dot{E} = \frac{4\pi^2 I \dot{P}}{P^3}, \qquad B_s = \sqrt{\frac{3 c^3 I}{8\pi^2 R^6} P \dot{P}} \approx 3.2 \times 10^{19} \sqrt{P \dot{P}}\text{ G}, \qquad \tau_c = \frac{P}{2\dot{P}}$$

Across the more than $3,500$ pulsars cataloged in the Australia Telescope National Facility (**ATNF**) Pulsar Catalogue, distinct astrophysical populations occupy separate regions of the $P\text{--}\dot{P}$ plane: young, energetic canonical pulsars, ultra-stable recycled millisecond pulsars (MSPs) spun up via binary accretion, strongly magnetized magnetars ($B_s \gtrsim 10^{14}\text{ G}$), and X-ray dim isolated neutron stars (XDINS).

This undergraduate thesis focuses on **observational catalog analysis, statistical subpopulation classification, and Monte Carlo evolutionary modeling of Galactic pulsars on the $P\text{--}\dot{P}$ diagram**. The scope encompasses three progressive stages:
1. **Programmatic Catalog Mining & Physical Parameter Inference:** Querying and filtering the live ATNF Pulsar Catalogue via Python (`psrqpy` / `astropy`) to compute derived magnetospheric parameters ($B_s, \tau_c, \dot{E}$, light-cylinder radius $R_{\text{LC}}$, and braking indices $n = \nu\ddot{\nu}/\dot{\nu}^2$ where $\ddot{P}$ is measured).
2. **Subpopulation Clustering & Death-Line Physics:** Applying statistical and unsupervised clustering techniques (Gaussian Mixture Models) to separate canonical pulsars, recycled MSPs, binary systems, and magnetars, while testing theoretical electron–positron pair-production "death lines" and "death valleys" (Chen & Ruderman 1993) along the lower-right boundary of the diagram.
3. **Evolutionary Tracks & Monte Carlo Population Synthesis:** Integrating spin-down differential equations ($\dot{P} \propto P^{2-n}$) under constant magnetic field vs. Ohmic/Hall magnetic field decay models, and constructing a forward Monte Carlo population synthesis simulation to evaluate how radio beaming fractions and survey sensitivity limits bias the observed $P\text{--}\dot{P}$ distribution.

Full 3D force-free magnetohydrodynamic (MHD) magnetospheric simulations, detailed binary stellar evolution tracks (mass-transfer Roche-lobe overflow hydrodynamics), and raw radio telescope baseband signal processing lie outside the scope of this project.

---

## 3. Objectives

### General Objective
To conduct a comprehensive observational and computational investigation of the Galactic pulsar population using the ATNF Pulsar Catalogue, classifying distinct neutron star subpopulations, evaluating theoretical pair-production death lines, and modeling spin-down evolutionary trajectories on the $P\text{--}\dot{P}$ diagram.

### Specific Objectives
1. **Automated ATNF Data Pipeline & Diagnostic Mapping:** Build a reproducible Python pipeline using `psrqpy` and `astropy` to ingest, clean, and cross-match timing, astrometric, binary, and multi-wavelength flags for $>3,500$ pulsars, computing canonical distributions of $P$, $\dot{P}$, $B_s$, $\tau_c$, $\dot{E}$, and dispersion-measure-derived Galactic scale heights ($|z|$).
2. **Statistical Subpopulation Classification:** Apply Gaussian Mixture Models (GMM) and kernel density estimation in the multi-dimensional parameter space $(\log P, \log \dot{P}, \log B_s)$ to objectively partition the pulsar zoo into canonical isolated pulsars, mildly recycled double neutron star (DNS) systems, fully recycled MSPs, and magnetars.
3. **Pulsar Death-Line & Braking-Index Evaluation:** Overlay theoretical curvature-radiation and inverse-Compton pair-production death lines onto the empirical $P\text{--}\dot{P}$ plane to test hypotheses for radio emission cessation, and analyze the subset of young pulsars with measured second period derivatives ($\ddot{P}$) to evaluate deviations from the canonical $n = 3$ vacuum dipole braking index.
4. **Magnetic Field Decay & Evolutionary Trajectory Modeling:** Numerically integrate coupled $(P(t), B_s(t))$ spin-down tracks comparing constant-dipole evolution against parametric Ohmic and Hall magnetic field decay models, tracing how young magnetars and canonical pulsars migrate across the $P\text{--}\dot{P}$ plane over $10^3\text{--}10^8\text{ yr}$.
5. **Monte Carlo Population Synthesis & Selection-Bias Quantification:** Implement a forward Monte Carlo simulation of synthetic Galactic pulsars drawn from birth spin-period and magnetic-field distributions, applying geometric beaming fractions $f(P)$ and radio flux-density detection thresholds to demonstrate how observational selection effects shape the observed $P\text{--}\dot{P}$ graveyard.

---

## 4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. **Open-Source Software Package (`pyPulsarPop`):**
   * A clean, modular, PEP-8 compliant Python package built on `NumPy`, `SciPy`, `Pandas`, `Astropy`, `psrqpy`, `scikit-learn`, and `Matplotlib`.
   * Modules for automated ATNF catalog querying and quality filtering, analytical spin-down parameter calculation, Gaussian Mixture Model classification, differential equation integrators for $(P(t), B(t))$ evolutionary tracks, and a Monte Carlo pulsar survey simulator.
   * Automated unit tests verifying unit conversions, braking-index analytical solutions, and flux-threshold filtering, paired with reproducible Jupyter notebooks generating all thesis figures.

2. **Scientific Visualization & Data Suite:**
   * High-resolution, publication-grade annotated $P\text{--}\dot{P}$ diagrams displaying constant-$B_s$, constant-$\tau_c$, and constant-$\dot{E}$ isolines, binary companions, supernova remnant associations, and pair-production death valleys.
   * Multi-panel statistical distributions (histograms, violin plots, and Galactic $|z|$-height correlations) contrasting young pulsars, MSPs, and magnetars.
   * Evolutionary track overlays comparing constant-$B$ vs. decaying-$B$ trajectories and side-by-side synthetic vs. observed $P\text{--}\dot{P}$ density maps from the Monte Carlo population synthesis.

3. **Undergraduate Thesis Manuscript & Defense:**
   * A formal LaTeX-typeset undergraduate thesis (40–60 pages) covering pulsar magnetospheric electrodynamics, statistical catalog methodology, evolutionary modeling, selection-bias analysis, and astrophysical discussion.
   * A 20-minute oral defense presentation summarizing the methodology, data analysis, simulation results, and conclusions.

---

## 5. 4 Months Timeline

The project is organized across **16 weeks (4 months)** into four structured monthly phases with concrete weekly milestones:

### Month 1: Magnetospheric Theory & ATNF Data Pipeline
* **Week 1:** Literature review of pulsar electrodynamics and spin-down theory (Pacini 1967; Goldreich & Julian 1969; Gunn & Ostriker 1969; Lorimer & Kramer 2004). Derive the vacuum magnetic dipole braking equations for $B_s$, $\tau_c$, $\dot{E}$, and braking index $n$.
* **Week 2:** Set up the Python environment (`psrqpy`, `astropy`, `pandas`) and query the live ATNF Pulsar Catalogue (Manchester et al. 2005). Implement filtering criteria to handle globular cluster pulsars affected by gravitational potential acceleration ($\dot{P}_{\text{obs}} < 0$).
* **Week 3:** Compute derived magnetospheric and energetic quantities ($B_s, \tau_c, \dot{E}, R_{\text{LC}}$, surface electric potential drop $\Delta \Phi$) across the validated sample and construct the baseline $P\text{--}\dot{P}$ visualization engine.
* **Week 4:** Analyze correlations between spin-down properties and Galactic kinematics (Galactic latitude $b$, dispersion-measure distance $d$, and scale height $|z| = d|\sin b|$), verifying the kinetic migration of older pulsars away from the Galactic plane.

### Month 2: Subpopulation Classification, Binary Systems & Death Lines
* **Week 5:** Apply unsupervised machine learning (`scikit-learn` Gaussian Mixture Models) in $(\log P, \log \dot{P})$ space to statistically separate canonical pulsars, recycled MSPs, and magnetars, evaluating optimal cluster counts via Bayesian Information Criterion (BIC).
* **Week 6:** Cross-match subpopulation classifications against ATNF binary flags, orbital periods ($P_b$), and minimum companion masses to map the recycling corridor linking Low-Mass X-Ray Binaries (LMXBs) to MSPs via the Eddington spin-up line.
* **Week 7:** Implement theoretical pulsar death lines and death valleys (Chen & Ruderman 1993; Zhang, Harding, & Muslimov 2000) based on polar-cap curvature radiation and inverse-Compton pair cascades, testing whether observed radio pulsars respect these boundaries.
* **Week 8:** Extract pulsars with reliable $\ddot{P}$ measurements and supernova remnant (SNR) associations, comparing characteristic ages $\tau_c$ against true SNR kinematic ages and measuring empirical braking indices $n \ne 3$.

### Month 3: Evolutionary Tracks & Monte Carlo Population Synthesis
* **Week 9:** Formulate and integrate differential spin-down equations $\dot{P}(t) = K B(t)^2 P(t)^{2-n}$ in Python (`scipy.integrate.solve_ivp`), contrasting constant-field trajectories ($n=3$) against variable braking indices ($n < 3$).
* **Week 10:** Implement parametric magnetic field decay models (exponential Ohmic decay and power-law Hall/ambipolar decay following Pons, Miralles, & Geppert 2009), tracing how high-$B$ pulsars and magnetars curve downward into the canonical pulsar island.
* **Week 11:** Build a forward Monte Carlo population synthesis simulator generating $10^5$ synthetic Galactic pulsars with log-normal birth spin periods ($P_0$), log-normal birth magnetic fields ($B_0$), and Galactic spatial distributions (Faucher-Giguère & Kaspi 2006).
* **Week 12:** Apply empirical radio beaming fraction models $f(P)$ (Tauris & Manchester 1998) and radio pseudo-luminosity scaling laws ($L_{1400} \propto P^\alpha \dot{P}^\beta$) with survey flux thresholds to isolate intrinsic vs. observable $P\text{--}\dot{P}$ distributions.

### Month 4: Synthesis, Benchmarking & Thesis Writing
* **Week 13:** Perform two-sample Kolmogorov–Smirnov (KS) tests comparing synthetic detected pulsar distributions against the observed ATNF catalog to constrain mean birth spin periods $\langle P_0 \rangle$ and magnetic field decay timescales $\tau_{\text{Ohm}}$.
* **Week 14:** Generate final publication-quality figures (annotated $P\text{--}\dot{P}$ diagram, GMM cluster contours, death-valley boundaries, decaying-$B$ tracks, and Monte Carlo synthetic distributions). Draft Chapters 1–3 of the thesis (Introduction, Theoretical Framework, Catalog Methodology).
* **Week 15:** Draft Chapters 4–5 (Statistical Results, Evolutionary Tracks, Population Synthesis, and Conclusions). Clean, document, and finalize the `pyPulsarPop` GitHub repository.
* **Week 16:** Advisor review, feedback integration, LaTeX typesetting polish, final thesis submission, and rehearsal of the 20-minute defense presentation.

---

## 6. References

1. **Pacini, F.** (1967). *Energy Emission from a Neutron Star*. Nature, 216(5115), 567–568.
2. **Goldreich, P., & Julian, W. H.** (1969). *Pulsar Electrodynamics*. The Astrophysical Journal, 157, 869–880.
3. **Gunn, J. E., & Ostriker, J. P.** (1969). *Magnetic Dipole Radiation from Pulsars*. Nature, 221(5179), 454–456.
4. **Alpar, M. A., Cheng, A. F., Ruderman, M. A., & Shaham, J.** (1982). *A new class of radio pulsars*. Nature, 300(5894), 728–730.
5. **Chen, K., & Ruderman, M.** (1993). *Pulsar Death Lines and Death Valley*. The Astrophysical Journal, 402, 264–270.
6. **Tauris, T. M., & Manchester, R. N.** (1998). *On the evolution of pulsar beams*. Monthly Notices of the Royal Astronomical Society, 298(3), 625–636.
7. **Lorimer, D. R., & Kramer, M.** (2004). *Handbook of Pulsar Astronomy*. Cambridge University Press.
8. **Manchester, R. N., Hobbs, G. B., Teoh, A., & Hobbs, M.** (2005). *The Australia Telescope National Facility Pulsar Catalogue*. The Astronomical Journal, 129(4), 1993–2006.
9. **Faucher-Giguère, C.-A., & Kaspi, V. M.** (2006). *Birth and Evolution of Isolated Radio Pulsars*. The Astrophysical Journal, 643(1), 332–355.
10. **Pons, J. A., Miralles, J. A., & Geppert, U.** (2009). *Magneto-thermal evolution of neutron stars*. Astronomy & Astrophysics, 496(1), 207–216.
11. **Bates, S. D., Lorimer, D. R., Rane, A., & Swiggum, J.** (2014). *PsrPopPy: An open-source package for pulsar population simulations*. Monthly Notices of the Royal Astronomical Society, 439(3), 2893–2902.
12. **Pitkin, M.** (2018). *psrqpy: a python interface for querying the ATNF pulsar catalogue*. Journal of Open Source Software, 3(22), 538.