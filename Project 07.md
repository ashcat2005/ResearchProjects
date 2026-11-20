Undergraduate Thesis Proposal

1. Title

Post-Glitch Rotational Relaxation Modeling and Crustal Superfluid Dynamics in Young Pulsars

2. Scope

While pulsars are renowned for their extraordinary rotational stability, young, energetic neutron stars (such as the Vela pulsar PSR B0833$-$45 and the Crab pulsar PSR B0531+21) periodically exhibit sudden, discrete spin-up events known as **pulsar glitches** ($\Delta \nu / \nu \sim 10^{-9}\text{ to }10^{-5}$), followed by a gradual, quasi-exponential recovery toward their pre-glitch spin-down trajectory. Within the standard two-component superfluid vortex-pinning paradigm (Baym et al. 1969; Anderson & Itoh 1975), a neutron star consists of an observable solid crust coupled to interior charged particles (moment of inertia $I_c$) and an interior neutron superfluid ($I_s$) threaded by quantized vortex lines. When vortices pinned to the inner crustal nuclear lattice catastrophically unpin, angular momentum is rapidly transferred to the crust, producing a spin-up glitch; subsequently, thermally activated vortex creep gradually re-establishes dynamical equilibrium between the superfluid and crust.

Following a glitch at epoch $t_g$, the post-glitch rotational frequency residual $\Delta \nu(t)$ relative to the pre-glitch spin-down ephemeris is modeled phenomenologically by a permanent step plus $N$ exponentially decaying components:

$$\Delta \nu(t) = \Delta \nu_p + \Delta \dot{\nu}_p (t - t_g) + \sum_{i=1}^{N} \Delta \nu_{d,i} \exp\left(-\frac{t - t_g}{\tau_{d,i}}\right)$$

Fitting this relaxation profile yields direct measurements of the healing parameter $Q = \sum \Delta \nu_{d,i} / \Delta \nu_{\text{total}}$, recovery timescales $\tau_{d,i}$, and the fractional moment of inertia carried by the superfluid reservoir ($I_s / I_{\text{total}} \ge \mathcal{G}$, the glitch activity parameter), providing a rare observational window into the nuclear physics of the inner neutron star crust.

This undergraduate thesis focuses on Bayesian parameter estimation of post-glitch rotational relaxation using public pulsar timing data and two-component superfluid modeling. The scope encompasses three progressive stages:

1. Timing Data Acquisition & Pre-Glitch Ephemeris Modeling: Retrieving public pulsar timing observations (Times of Arrival, TOAs, or spin-frequency time series) from open pulsar timing archives (Jodrell Bank glitch catalogue, Fermi-LAT $\gamma$-ray timing datasets, and UTMOST / Parkes public releases) for high-activity glitching pulsars (specifically Vela and Crab, plus comparison objects like PSR J0537$-$6910).

2. Bayesian Post-Glitch Relaxation Fitting: Implementing Markov Chain Monte Carlo (MCMC) inference (emcee) with model selection (Bayesian Information Criterion / Bayes factors) to fit single- and multi-exponential recovery models, disentangling red timing noise from true post-glitch exponential relaxation.

3. Two-Component Superfluid & Equation of State Constraints: Mapping fitted glitch amplitudes, healing parameters $Q$, and recovery timescales $\tau_d$ onto the analytical two-component superfluid equations to infer crustal superfluid fractional moments of inertia ($I_{\text{crust}} / I_{\text{total}}$) and benchmark these bounds against theoretical Equation of State (EoS) predictions (incorporating crustal entrainment corrections).

Raw radio telescope baseband dedispersion, relativistic binary orbital timing models, and non-linear 3D Gross–Pitaevskii quantum vortex simulations lie outside the scope of this project.

3. Objectives

General Objective

To develop, validate, and apply a Bayesian pulsar timing and post-glitch relaxation analysis pipeline in Python to extract recovery timescales and healing parameters from archival observations of young pulsars, thereby constraining the fractional moment of inertia of the crustal neutron superfluid.

Specific Objectives

1. Timing Residual & Ephemeris Pipeline: Build a Python data-ingestion and timing-residual workflow utilizing PINT / Astropy to process public TOA datasets and spin-frequency histories for selected glitching pulsars (Vela PSR B0833$-$45 and Crab PSR B0531+21), fitting pre-glitch Taylor-series spin-down ephemerides ($\nu_0, \dot{\nu}_0, \ddot{\nu}_0$).

2. Synthetic Glitch Injection & Recovery Validation: Construct a synthetic TOA/frequency simulator incorporating realistic measurement uncertainties, uneven observational cadence, and red timing noise to verify that the MCMC fitting algorithm recovers injected glitch parameters ($\Delta \nu_p, \Delta \dot{\nu}_p, \Delta \nu_{d,i}, \tau_{d,i}$) without bias.

3. Bayesian MCMC Relaxation Modeling: Apply ensemble MCMC sampling (emcee) across multiple historical glitch epochs in Vela and Crab, testing $N = 0, 1, 2$ exponential recovery components and quantifying posterior uncertainties and parameter degeneracies (particularly between $\Delta \nu_d$ and $\tau_d$ when observational cadence is sparse immediately post-glitch).

4. Superfluid Reservoir & Crustal Moment of Inertia Inference: Compute cumulative glitch activity parameters $\mathcal{G} = \frac{1}{\Delta T} \sum \frac{\Delta \nu_i}{\nu}$ and healing parameters $Q$ across multi-decade glitch histories (via the Jodrell Bank Glitch Catalogue) to place lower bounds on the crustal superfluid moment of inertia fraction $I_{\text{sf}} / I_{\text{total}}$, accounting for Chamel's crustal entrainment factor.

5. Comparative Pulsar & EoS Synthesis: Contrast the relaxation behavior of Vela-like pulsars (large glitches, rapid multi-timescale recovery) against Crab-like pulsars (smaller glitches, persistent $\Delta \dot{\nu}_p$ shifts), comparing inferred $I_{\text{crust}} / I_{\text{total}}$ bounds against theoretical values computed from soft vs. stiff nuclear Equations of State.

4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. Open-Source Software Package (pyGlitchFit):

	⚬ A clean, modular, PEP-8 compliant Python package built on NumPy, SciPy, Astropy, PINT, emcee, corner, and Matplotlib.

	⚬ Modules for ingesting public .tim/.par files and Jodrell Bank glitch tables, computing phase/frequency timing residuals, simulating noisy synthetic glitches, and running multi-component Bayesian MCMC post-glitch relaxation fits.

	⚬ Automated unit tests verifying analytical two-component superfluid ODE solutions and synthetic parameter recovery, accompanied by reproducible Jupyter notebooks generating all thesis figures.

2. Scientific Visualization & Data Suite:

	⚬ High-resolution timing residual plots ($\Delta \phi(t)$ and $\Delta \nu(t)$) illustrating pre-glitch spin-down, instantaneous glitch jumps, and post-glitch exponential recovery curves with $1\sigma$ and $2\sigma$ posterior credible bands.

	⚬ Corner plots of MCMC posterior probability distributions highlighting parameter correlations and Bayes-factor model comparisons ($1$-exponential vs. $2$-exponential models).

	⚬ Cumulative glitch spin-up staircase plots ($\sum \Delta \nu / \nu$ vs. time) for Vela, Crab, and PSR J0537$-$6910, alongside theoretical $I_{\text{crust}} / I_{\text{total}}$ vs. Neutron Star Mass curves confronting observational lower bounds.

3. Undergraduate Thesis Manuscript & Defense:

	⚬ A formal LaTeX-typeset undergraduate thesis (40–60 pages) detailing neutron star interior superfluidity, pulsar timing methodology, Bayesian MCMC inference, empirical glitch fitting results, and nuclear EoS implications.

	⚬ A 20-minute oral defense presentation summarizing the theoretical background, statistical methodology, observational fits, and physical conclusions.

5. 4 Months Timeline

The project is organized across 16 weeks (4 months) into four structured monthly phases with concrete weekly milestones:

Month 1: Superfluid Glitch Theory & Timing Infrastructure

⚬ Week 1: Literature review of pulsar glitches and superfluid dynamics (Baym et al. 1969; Anderson & Itoh 1975; Alpar et al. 1984; Haskell & Melatos 2015). Derive the coupled two-component linear differential equations for crustal ($\Omega_c$) and superfluid ($\Omega_s$) angular velocities.

⚬ Week 2: Set up the Python timing environment (PINT, astropy, emcee, corner) and download archival glitch catalogs (Jodrell Bank Glitch Catalogue; Espinoza et al. 2011) alongside public Fermi-LAT and UTMOST TOA datasets for Vela and Crab.

⚬ Week 3: Implement pre-glitch ephemeris fitting ($\nu(t) = \nu_0 + \dot{\nu}_0(t - t_0) + \frac{1}{2}\ddot{\nu}_0(t - t_0)^2$) and verify phase-connected timing residual extraction across pre-glitch baseline windows.

⚬ Week 4: Build the forward analytical two-component relaxation simulator and verify that numerical integration of the coupled $(\Omega_c, \Omega_s)$ ODEs reproduces the exact exponential recovery formula $\Delta \nu(t) = \Delta \nu_p + \Delta \nu_d e^{-t/\tau_d}$.

Month 2: Synthetic Validation & Bayesian MCMC Pipeline

⚬ Week 5: Formulate the Bayesian likelihood function for post-glitch frequency and phase residuals, incorporating white measurement errors and an extra jitter/red-noise variance parameter ($\sigma_{\text{jit}}$).

⚬ Week 6: Implement the ensemble MCMC sampler (emcee) with physically motivated uniform/log-uniform priors for $\Delta \nu_p$, $\Delta \dot{\nu}_p$, $\Delta \nu_{d,i}$, and $\tau_{d,i}$.

⚬ Week 7: Conduct end-to-end synthetic injection-and-recovery tests across varying observational cadences (daily vs. weekly TOAs) and signal-to-noise ratios to quantify parameter biases and minimum resolvable recovery timescales $\tau_{d,\text{min}}$.

⚬ Week 8: Implement Bayesian model comparison metrics (BIC, AIC, and thermodynamic integration / nested sampling via dynesty) to objectively distinguish single-exponential from double-exponential recovery regimes.

Month 3: Archival Pulsar Glitch Modeling & Superfluid Constraints

⚬ Week 9: Apply the validated MCMC pipeline to major historical glitches of the Vela pulsar (PSR B0833$-$45) (e.g., the 2000, 2004, and 2016 glitches), extracting short-timescale ($\tau_{d,1} \sim \text{hours--days}$) and intermediate-timescale ($\tau_{d,2} \sim \text{weeks}$) recovery components.

⚬ Week 10: Apply the pipeline to historical glitches of the Crab pulsar (PSR B0531+21) (e.g., the 1975, 1989, and 2017 glitches), quantifying persistent post-glitch spin-down rate offsets ($\Delta \dot{\nu}_p < 0$) and lower healing parameters $Q$.

⚬ Week 11: Perform linear regression on cumulative glitch spin-up histories across multi-decade baselines for Vela, Crab, and PSR J0537$-$6910 to measure empirical glitch activity parameters $\mathcal{G}$ and infer minimum superfluid fractional moments of inertia $I_{\text{sf}} / I_{\text{total}}$.

⚬ Week 12: Evaluate the impact of crustal entrainment (Chamel 2013; Andersson et al. 2012) on the inferred moment-of-inertia bound, comparing observational limits against theoretical $I_{\text{crust}} / I_{\text{total}}$ curves from standard nuclear EoSs (SLy4, APR4).

Month 4: Synthesis, Visualization & Thesis Writing

⚬ Week 13: Synthesize cross-pulsar comparisons (Vela vs. Crab vs. PSR J0537$-$6910) correlating glitch size, healing parameter $Q$, and characteristic age $\tau_c$, evaluating how internal temperature governs vortex creep timescales.

⚬ Week 14: Generate publication-grade thesis figures (timing residual fits, MCMC corner plots, cumulative activity staircases, and crustal moment-of-inertia constraints). Draft Chapters 1–3 of the thesis (Introduction, Superfluid Theory, Bayesian Timing Methodology).

⚬ Week 15: Draft Chapters 4–5 (Vela & Crab Fitting Results, Crustal Superfluid Constraints, Discussion, and Conclusions). Clean, document, and finalize the pyGlitchFit GitHub repository.

⚬ Week 16: Advisor review, feedback integration, LaTeX typesetting polish, final thesis submission, and rehearsal of the 20-minute defense presentation.

6. References

1. Baym, G., Pethick, C., Pines, D., & Ruderman, M. (1969). Spin Up in Neutron Stars: The Future of the Vela Pulsar. Nature, 224(5222), 872–874.

2. Anderson, P. W., & Itoh, N. (1975). Pulsar glitches and restlessness as a hard superfluidity phenomenon. Nature, 256(5512), 25–27.

3. Alpar, M. A., Pines, D., Anderson, P. W., & Shaham, J. (1984). Vortex creep and the internal temperature of neutron stars. I. General theory. The Astrophysical Journal, 276, 325–334.

4. Link, B., Epstein, R. I., & Lattimer, J. M. (1999). Pulsar Constraints on Neutron Star Structure and Equation of State. Physical Review Letters, 83(17), 3362–3365.

5. Dodson, R. G., McCulloch, P. M., & Lewis, D. R. (2002). High Time Resolution Observations of the January 2000 Glitch in the Vela Pulsar. The Astrophysical Journal Letters, 564(2), L85–L88.

6. Espinoza, C. M., Lyne, A. G., Stappers, B. W., & Kramer, M. (2011). A study of 315 glitches in the rotation of 102 pulsars. Monthly Notices of the Royal Astronomical Society, 414(2), 1679–1704.

7. Andersson, N., Glampedakis, K., Ho, W. C. G., & Espinoza, C. M. (2012). Pulsar Glitches: The Crust is not Enough. Physical Review Letters, 109(24), 241103.

8. Chamel, N. (2013). Crustal Entrainment and Pulsar Glitches. Physical Review Letters, 110(1), 011101.

9. Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. (2013). emcee: The MCMC Hammer. Publications of the Astronomical Society of the Pacific, 125(925), 306–312.

10. Haskell, B., & Melatos, A. (2015). Models of pulsar glitches. International Journal of Modern Physics D, 24(03), 1530008.

11. Lower, M. E., et al. (2021). The UTMOST pulsar timing programme – II. Glitch recovery and timing noise in young pulsars. Monthly Notices of the Royal Astronomical Society, 508(3), 3251–3274.

12. Luo, J., et al. (2021). PINT: A Modern Software Package for Pulsar Timing. The Astrophysical Journal, 911(1), 45.
