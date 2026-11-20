# Undergraduate Thesis Proposal

## 1. Title
**Time-Resolved Hard X-Ray Spectroscopy and Trapped-Fireball Diagnostics of Magnetar Short Bursts with *Fermi*-GBM**

---

## 2. Scope
Magnetars—isolated neutron stars powered by the decay of ultra-strong internal magnetic fields ($B \sim 10^{14}\text{--}10^{15}\text{ G}$)—exhibit dramatic high-energy radiative variability, most notably recurrent, sub-second bursts of hard X-rays and soft $\gamma$-rays with peak luminosities $L \sim 10^{38}\text{--}10^{41}\text{ erg s}^{-1}$. Within the standard magnetar paradigm (Thompson & Duncan 1995), internal magnetic stresses fracture or plastically deform the solid neutron star crust, launching relativistic Alfvén waves into the closed magnetosphere. Magnetic reconnection and pair-production cascades subsequently trap an optically thick electron–positron ($e^\pm$) pair plasma within closed magnetic flux tubes—a "trapped fireball"—whose photospheric cooling emits thermalized hard X-ray radiation.

Assuming isotropic thermal emission from a localized magnetospheric photosphere at distance $D$, the observed bolometric blackbody flux $F_{\text{BB}}$ and color temperature $kT$ yield an effective blackbody emitting radius $R_{\text{BB}}$:

$$F_{\text{BB}} = \frac{L_{\text{BB}}}{4\pi D^2} = \left(\frac{R_{\text{BB}}}{D}\right)^2 \sigma_{\text{SB}} T^4$$

Tracking how spectral parameters ($kT$, $R_{\text{BB}}$, and non-thermal power-law photon indices) evolve on millisecond timescales during individual bursts provides direct observational diagnostics of trapped-fireball expansion, magnetic confinement, and Compton scattering in super-Schwinger magnetic fields ($B > B_{\text{QED}} \approx 4.4 \times 10^{13}\text{ G}$).

This undergraduate thesis focuses on **temporal and time-resolved spectral analysis of magnetar short bursts using archival Time-Tagged Event (TTE) data from NASA's *Fermi* Gamma-ray Burst Monitor (GBM)**. The scope encompasses three progressive stages:
1. **Event Selection & Temporal Characterization:** Querying NASA's High Energy Astrophysics Science Archive Research Center (**HEASARC**) for public *Fermi*-GBM TTE data and Detector Response Matrices (DRMs) of prolific burst-forest magnetars—specifically **SGR J1935+2154** (including its 2020 burst storm associated with Fast Radio Burst FRB 200428) and **SGR J1550$-$5418**—and measuring model-independent burst durations ($T_{90}, T_{50}$) and hardness ratios via Bayesian Blocks segmentation.
2. **Forward-Folding Time-Integrated Spectral Modeling:** Fitting polynomial background models and convolving candidate photon models—Single Blackbody (`BB`), Two-Blackbody (`BB+BB`), Comptonized/Cutoff Power-Law (`COMP`), and Optically Thin Thermal Bremsstrahlung (`OTTB`)—through GBM NaI detector response matrices ($8\text{--}1000\text{ keV}$) via Cash-statistic (`pgstat`) minimization.
3. **Time-Resolved Spectroscopy & Fireball Scaling Relations:** Partitioning bright bursts into fine temporal bins ($10\text{--}32\text{ ms}$) to track intra-burst spectral evolution and test correlations between burst luminosity, blackbody temperatures ($kT_{\text{cool}}, kT_{\text{hot}}$), and emitting areas ($R_{\text{BB}}^2$), contrasting standard bursts against the FRB-associated X-ray burst of SGR J1935+2154.

Giant flares exhibiting detector pulse pile-up and telemetry saturation, raw spacecraft attitude/ephemeris reconstruction, and 3D quantum electrodynamic (QED) Monte Carlo radiative transfer simulations lie outside the scope of this project.

---

## 3. Objectives

### General Objective
To develop, validate, and apply a reproducible *Fermi*-GBM temporal and spectral analysis pipeline in Python to characterize the time-integrated and time-resolved hard X-ray properties of magnetar short bursts, testing thermal trapped-fireball emission models against non-thermal Comptonized spectra.

### Specific Objectives
1. **HEASARC Data Ingestion & Bayesian Blocks Timing Pipeline:** Build an automated Python workflow utilizing the official *Fermi* Gamma-ray Data Tools (`gdt-fermi` / `astropy`) to retrieve TTE photon lists and DRM files for selected burst episodes of **SGR J1935+2154** and **SGR J1550$-$5418**, extracting multi-detector light curves and measuring $T_{90}$ and $T_{50}$ durations via Scargle's Bayesian Blocks algorithm.
2. **Detector Background & Forward-Folding Spectral Framework:** Implement polynomial background interpolation across pre- and post-burst intervals and establish a forward-folding spectral fitting routine (`gdt-fermi` / `3ML` / `PyXspec`) across bright NaI detectors ($8\text{--}900\text{ keV}$), accounting for the iodine K-edge ($33.17\text{ keV}$) and Bismuth Germanate (BGO) upper-energy limits.
3. **Time-Integrated Spectral Model Comparison:** Fit `BB`, `BB+BB`, `COMP`, and `OTTB` photon models to a sample of $\ge 25$ bright short bursts, using Bayesian Information Criterion ($\Delta\text{BIC}$) and goodness-of-fit posterior predictive checks to determine whether two-temperature thermal or Comptonized models statistically dominate.
4. **Intra-Burst Time-Resolved Spectroscopy:** Subdivide the brightest bursts ($\ge 500$ net counts) into signal-to-noise-adaptive or Bayesian-Block time slices ($8\text{--}32\text{ ms}$ resolution) to trace temporal evolution of $kT$, $R_{\text{BB}}$, hardness ratios, and spectral lags across burst rise, peak, and decay phases.
5. **Statistical Scaling & FRB-Burst Comparison:** Evaluate ensemble correlations across the burst sample—specifically the $L_{\text{BB}}\text{--}kT$ and $R_{\text{BB}}^2\text{--}kT$ relations—and compare the spectral hardness and non-thermal tail of SGR J1935+2154's FRB 200428-associated X-ray burst against ordinary magnetar bursts.

---

## 4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. **Open-Source Software Package (`pyMagBurst`):**
   * A clean, modular, PEP-8 compliant Python package built on `NumPy`, `SciPy`, `Astropy`, `gdt-core` / `gdt-fermi`, `emcee`, and `Matplotlib`.
   * Modules for querying HEASARC GBM trigger/continuous TTE archives, automated detector angle selection (selecting NaI detectors with source off-axis angle $< 60^\circ$), Bayesian Blocks $T_{90}$ calculation, background polynomial fitting, and forward-folding spectral fitting.
   * Automated unit tests verifying DRM forward-folding matrix multiplication, blackbody flux normalization, and synthetic Poisson count-spectrum recovery, accompanied by reproducible Jupyter notebooks generating all thesis figures.

2. **Scientific Visualization & Data Suite:**
   * Multi-detector light curves with Bayesian Blocks change-point overlays, $T_{90}$ intervals, and energy-resolved hardness-ratio evolution tracks.
   * Count-space and deconvolved $\nu F_\nu$ spectral fit plots with residuals comparing `BB`, `BB+BB`, and `COMP` models for representative magnetar bursts.
   * Time-resolved evolution tracks of $kT(t)$ and $R_{\text{BB}}(t)$ during bright bursts, alongside ensemble scatter plots of blackbody emitting area ($R_{\text{BB}}^2$) vs. temperature ($kT$) and fluence–duration distributions.

3. **Undergraduate Thesis Manuscript & Defense:**
   * A formal LaTeX-typeset undergraduate thesis (40–60 pages) covering magnetar magnetospheric physics, *Fermi*-GBM instrumentation and detector response forward-folding, statistical timing/spectral methodology, empirical burst results, and astrophysical implications.
   * A 20-minute oral defense presentation summarizing the theoretical background, data analysis pipeline, observational findings, and conclusions.

---

## 5. 4 Months Timeline

The project is organized across **16 weeks (4 months)** into four structured monthly phases with concrete weekly milestones:

### Month 1: Magnetar Theory, *Fermi*-GBM Instrumentation & Timing Pipeline
* **Week 1:** Literature review of magnetar burst physics and trapped fireballs (Duncan & Thompson 1992; Thompson & Duncan 1995; Israel et al. 2008; Kaspi & Beloborodov 2017) alongside *Fermi*-GBM instrument mechanics (Meegan et al. 2009).
* **Week 2:** Set up the Python high-energy astrophysics stack (`gdt-fermi`, `astropy`, `scipy`, `emcee`) and download public TTE data and DRM files from HEASARC for selected bursts of **SGR J1935+2154** (2020 burst storm) and **SGR J1550$-$5418** (2009 burst forest).
* **Week 3:** Implement automated detector geometry selection (filtering NaI detectors with viewing angles $< 60^\circ$ and no spacecraft blockage) and construct energy-resolved light curves ($8\text{--}50\text{ keV}$ soft vs. $50\text{--}300\text{ keV}$ hard bands).
* **Week 4:** Implement Scargle's Bayesian Blocks segmentation algorithm (`astropy.stats.bayesian_blocks`) to objectively detect burst intervals, measure $T_{90}$ and $T_{50}$ durations, and compute background-subtracted hardness ratios.

### Month 2: Forward-Folding Spectral Engine & Validation
* **Week 5:** Formulate the forward-folding spectral fitting equations mapping theoretical photon flux $N(E; \boldsymbol{\theta})$ through the GBM Detector Response Matrix $R_{ij}$ to expected detector counts $C_i$, implementing the Poisson-Gaussian (`pgstat`) likelihood function.
* **Week 6:** Code analytical photon spectral models (`BB`, `BB+BB`, `COMP`, and `OTTB`) in Python and verify accurate convolution against synthetic count spectra generated with known input parameters.
* **Week 7:** Implement polynomial background fitting across pre- and post-burst time windows, validating background-interpolated uncertainties across the $8\text{--}900\text{ keV}$ NaI bandpass (excluding the $30\text{--}40\text{ keV}$ iodine K-edge calibration feature).
* **Week 8:** Benchmark the pipeline by reproducing published spectral parameters for a canonical bright burst from **SGR J1550$-$5418** (van der Horst et al. 2012), confirming agreement within $1\sigma$ uncertainties.

### Month 3: Ensemble Burst Fitting & Time-Resolved Spectroscopy
* **Week 9:** Execute batch time-integrated spectral fits across the curated sample of $\ge 25$ bursts from SGR J1935+2154 and SGR J1550$-$5418, computing $\Delta\text{BIC}$ model preference metrics between `BB`, `BB+BB`, and `COMP` models.
* **Week 10:** Derive bolometric fluxes, isotropic-equivalent energies ($E_{\text{iso}}$), and effective blackbody emitting radii ($R_{\text{BB, cool}}, R_{\text{BB, hot}}$) using standard source distances ($D \approx 9\text{ kpc}$ for SGR J1935+2154; $D \approx 4.5\text{ kpc}$ for SGR J1550$-$5418).
* **Week 11:** Perform fine time-resolved spectroscopy ($8\text{--}32\text{ ms}$ bins) on the brightest bursts in the sample, tracking intra-burst evolution of blackbody temperatures and emitting areas to test trapped-fireball expansion and cooling predictions.
* **Week 12:** Analyze the specific *Fermi*-GBM burst from **SGR J1935+2154** associated with FRB 200428 (2020 April 28; Lin et al. 2020), comparing its spectral cutoff energy and hardness ratio against the broader non-FRB burst population.

### Month 4: Statistical Synthesis & Thesis Writing
* **Week 13:** Perform ensemble correlation analyses ($L_{\text{BB}}$ vs. $kT$, $R_{\text{BB}}^2$ vs. $kT$, and hardness–intensity correlations) using MCMC linear regression accounting for bivariate measurement errors.
* **Week 14:** Generate publication-grade thesis figures (multi-band light curves with Bayesian Blocks, $\nu F_\nu$ spectral fit comparisons, time-resolved $kT(t)/R_{\text{BB}}(t)$ tracks, and $R_{\text{BB}}^2\text{--}kT$ scaling plots). Draft Chapters 1–3 of the thesis (Introduction, Magnetar Physics, GBM Spectral Methodology).
* **Week 15:** Draft Chapters 4–5 (Time-Integrated & Time-Resolved Results, FRB Comparison, Discussion, and Conclusions). Clean, document, and finalize the `pyMagBurst` GitHub repository.
* **Week 16:** Advisor review, feedback integration, LaTeX typesetting polish, final thesis submission, and rehearsal of the 20-minute defense presentation.

---

## 6. References

1. **Duncan, R. C., & Thompson, C.** (1992). *Formation of Very Strongly Magnetized Neutron Stars: Implications for Gamma-Ray Bursts*. The Astrophysical Journal Letters, 392, L9–L13.
2. **Thompson, C., & Duncan, R. C.** (1995). *The soft gamma repeaters as very strongly magnetized neutron stars – I. Radiative mechanism for outbursts*. Monthly Notices of the Royal Astronomical Society, 275(2), 255–300.
3. **Israel, G. L., et al.** (2008). *A Swift Gaze into the 2006 March 29 Outburst of SGR 1900+14*. The Astrophysical Journal, 685(2), 1114–1128.
4. **Meegan, C., et al.** (2009). *The Fermi Gamma-ray Burst Monitor*. The Astrophysical Journal, 702(1), 791–804.
5. **van der Horst, A. J., et al.** (2012). *SGR J1550$-$5418 Bursts Detected with the Fermi Gamma-Ray Burst Monitor during its Most Prolific Activity*. The Astrophysical Journal, 749(2), 122.
6. **Scargle, J. D., Norris, J. P., Jackson, B., & Chiang, J.** (2013). *Studies in Astronomical Time Series Analysis. VI. Bayesian Block Representations*. The Astrophysical Journal, 764(2), 167.
7. **Collazzi, A. C., et al.** (2015). *The Five Year Fermi/GBM Magnetar Burst Catalog*. The Astrophysical Journal Supplement Series, 218(1), 11.
8. **Kaspi, V. M., & Beloborodov, A. M.** (2017). *Magnetars*. Annual Review of Astronomy and Astrophysics, 55, 261–301.
9. **Lin, L., et al.** (2020). *No pulsed radio emission during a bursting phase of a Galactic magnetar*. Nature, 587(7832), 63–65.
10. **Mereghetti, S., et al.** (2020). *INTEGRAL Discovery of a Burst with Associated Radio Emission from the Magnetar SGR 1935+2154*. The Astrophysical Journal Letters, 898(2), L29.
11. **Goldstein, A., Cleveland, W. H., & Kocevski, D.** (2022). *Fermi Gamma-ray Data Tools: A Python Toolkit for Fermi Gamma-ray Burst Monitor Data Analysis*. Zenodo / Astrophysics Source Code Library (ascl:2304.011).