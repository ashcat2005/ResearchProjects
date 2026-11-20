# Undergraduate Thesis Proposal

## 1. Title
**Tidal Deformability and the Quadrupolar Love Number ($k_2$) of Neutron Stars in Binary Inspirals**

---

## 2. Scope
During the late inspiral phase of a binary neutron star (BNS) coalescence, each star experiences an increasingly strong external tidal gravitational field $\mathcal{E}_{ij}$ exerted by its companion. In response, the neutron star develops an induced mass quadrupole moment $Q_{ij}$. To leading adiabatic order, these quantities are linearly related via the tidal deformability parameter $\lambda$:

$$Q_{ij} = -\lambda\,\mathcal{E}_{ij}$$

This tidal response imprints a characteristic phase shift onto the emitted gravitational waveform, making the dimensionless tidal deformability $\Lambda = \lambda c^{10} / (G^4 M^5)$ a direct, clean probe of the unknown dense-matter Equation of State (EoS) at supranuclear densities. Following the landmark detection of **GW170817** by the LIGO–Virgo collaboration, measurements of $\Lambda$ have become one of the most powerful observational constraints on nuclear physics.

This undergraduate thesis focuses on computing the relativistic **even-parity, static quadrupolar ($l = 2$) tidal Love number $k_2$** and dimensionless tidal deformability $\Lambda$ for non-rotating, cold ($T = 0$), spherically symmetric neutron stars. The framework extends the standard Tolman–Oppenheimer–Volkoff (TOV) stellar structure equations by coupling them to the linearized Einstein field equations for static quadrupolar metric perturbations $H(r)$, formulated as a first-order Riccati differential equation for the logarithmic derivative $y(r) = r H'(r) / H(r)$.

The scope encompasses:
1. **Relativistic Perturbation Formulation:** Deriving and numerically integrating the coupled TOV + tidal perturbation system for both continuous and discontinuous density profiles (handling sharp density jumps at the core–crust boundary or phase transitions).
2. **EoS Exploration:** Evaluating $k_2$ and $\Lambda$ across analytical relativistic polytropes, incompressible fluid spheres, and tabulated nuclear EoSs ranging from soft to stiff (e.g., **SLy4**, **APR4**, **DD2**, and **MS1**).
3. **Gravitational-Wave Observational Benchmarking:** Comparing theoretical tidal deformability curves $\Lambda(M)$ and binary effective tidal deformability $\tilde{\Lambda}$ against LIGO/Virgo posterior bounds from **GW170817** ($\Lambda_{1.4} \le 800$ at 90% confidence) and **GW190425**, as well as testing quasi-universal relations (such as the $I\text{--Love--}Q$ or $C\text{--}\Lambda$ relations).

Dynamical tides (resonant $f$-mode excitation near merger), spin–tidal couplings, and magnetic or elastic crustal shear corrections lie outside the scope of this project.

---

## 3. Objectives

### General Objective
To develop, validate, and apply a coupled general relativistic stellar structure and tidal perturbation solver in Python to compute the quadrupolar Love number $k_2$ and dimensionless tidal deformability $\Lambda$ of neutron stars, and to constrain viable nuclear Equations of State using LIGO/Virgo gravitational-wave observations.

### Specific Objectives
1. **Coupled Differential System Implementation:** Formulate the coupled system of ordinary differential equations governing hydrostatic equilibrium ($P(r)$, $m(r)$) and static $l=2$ metric perturbations ($y(r)$), implementing a high-precision numerical integrator (RK4 / adaptive `RK45`) in Python with proper central boundary conditions ($y(0) = 2$).
2. **Code Verification & Discontinuity Treatment:** Validate the solver against the exact analytical limit for an incompressible constant-density sphere ($C \to 0$ Newtonian limit $k_2 = 3/4$, and full relativistic incompressible solution including the surface density-jump junction condition $\Delta y = -4\pi R^3 \epsilon_s / M$).
3. **EoS Dependence of $k_2$ and $\Lambda$:** Compute $k_2(M)$, $\lambda(M)$, and $\Lambda(M)$ across relativistic polytropes ($\Gamma \in [1.5, 3.0]$) and realistic tabulated nuclear EoSs (SLy4, APR4, DD2, MS1), isolating how core stiffness and crustal thickness affect tidal deformability.
4. **Universal Relations Analysis:** Test the quasi-universal relation between stellar compactness $C = GM / (Rc^2)$ and dimensionless tidal deformability $\Lambda$ across diverse EoSs, quantifying fractional deviations from the Yagi–Yunes analytical fit.
5. **Binary Gravitational-Wave Constraints:** Compute the mass-weighted binary tidal deformability $\tilde{\Lambda}$ across compatible component masses $(m_1, m_2)$ for **GW170817** (given its measured chirp mass $\mathcal{M} = 1.186\,M_{\odot}$) to systematically test and rule out overly stiff nuclear EoS models.

---

## 4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. **Open-Source Software Package (`pyTidalNS`):**
   * A modular, well-documented Python package built on `NumPy`, `SciPy`, and `Matplotlib`.
   * Solvers for the baseline TOV equations and the coupled $l=2$ tidal perturbation Riccati equation, including explicit junction-condition handling for first-order density discontinuities.
   * Automated EoS interpolation routines (log-log cubic splines and adiabatic sound-speed derivatives $d\epsilon/dP$) and binary $\tilde{\Lambda}(q)$ calculators.
   * Unit test suite validating convergence rates and exact reproduction of analytical incompressible Love numbers, accompanied by reproducible Jupyter notebooks.

2. **Scientific Visualization & Data Suite:**
   * Radial internal profiles of the metric perturbation function $H(r)$ and logarithmic derivative $y(r)$ from center to surface across varying compactness values.
   * Curves of quadrupolar Love number $k_2$ vs. compactness $C$ and dimensionless tidal deformability $\Lambda$ vs. gravitational mass $M$ across multiple nuclear EoSs.
   * Binary tidal deformability $\tilde{\Lambda}$ vs. mass ratio $q = m_2/m_1$ curves benchmarked directly against LIGO/Virgo **GW170817** 90% credible upper limits, alongside $C\text{--}\Lambda$ universal relation residual plots.

3. **Undergraduate Thesis Manuscript & Defense:**
   * A formal LaTeX-typeset undergraduate thesis (40–60 pages) detailing relativistic perturbation theory, numerical implementation, code verification, physical results, and gravitational-wave implications.
   * A 20-minute oral defense presentation summarizing the methodology, results, and conclusions.

---

## 5. 4 Months Timeline

The project is organized over **16 weeks (4 months)** into four structured monthly phases with clear weekly milestones:

### Month 1: Relativistic Tidal Theory & Baseline TOV Solver
* **Week 1:** Literature review of relativistic tidal perturbations (Hinderer 2008; Binnington & Poisson 2009; Damour & Nagar 2009). Review the multipole expansion of the external gravitational potential and the definition of $k_2$ and $\Lambda$.
* **Week 2:** Derive the linearized Einstein field equations for static, even-parity $l=2$ perturbations of a spherically symmetric spacetime, reducing the second-order ODE for $H(r)$ into the first-order Riccati equation for $y(r)$.
* **Week 3:** Implement and verify the baseline dimensionless TOV solver in Python (`RK4` / `RK45`), confirming accurate $M\text{--}R$ curves for polytropic EoSs.
* **Week 4:** Couple the $y(r)$ differential equation to the TOV integrator, implementing the small-$r$ Taylor series boundary conditions ($y(0) = 2 + O(r^2)$) and algebraic evaluation of $k_2(C, y_R)$ at the stellar surface $r = R$.

### Month 2: Analytical Validation & Density Discontinuities
* **Week 5:** Derive and implement the surface junction condition $\Delta y = -4\pi R^3 \epsilon(R^-) / M$ required when energy density does not vanish smoothly at the stellar surface.
* **Week 6:** Validate the solver against the analytical constant-density incompressible sphere across compactness $C \in (0, 4/9)$, reproducing the Newtonian limit $k_2 \to 3/4$ as $C \to 0$ and the relativistic suppression $k_2 \to 0$ as $C \to 4/9$ (black hole limit).
* **Week 7:** Run parameter sweeps for relativistic polytropes ($P = K\rho^{\Gamma}$) across varying adiabatic indices ($\Gamma = 1.5, 2.0, 2.5, 3.0$), analyzing how central condensation reduces $k_2$ while increasing radius and $\Lambda$.
* **Week 8:** Investigate the sensitivity of $k_2$ and $\Lambda$ to the numerical evaluation of the derivative $d\epsilon/dP = c^2 / c_s^2$, comparing analytical derivatives against finite-difference and spline approximations.

### Month 3: Realistic Nuclear EoSs & Universal Relations
* **Week 9:** Download tabulated microphysical nuclear EoSs (SLy4, APR4, DD2, MS1) from public repositories (CompOSE). Implement smooth, thermodynamically consistent cubic spline interpolation for $P(\epsilon)$ and $d\epsilon/dP$.
* **Week 10:** Compute complete sequences of $k_2(M)$, $\lambda(M)$, and $\Lambda(M)$ for all tabulated EoSs across stable central densities, extracting canonical values $k_{2, 1.4}$ and $\Lambda_{1.4}$ at $M = 1.4\,M_{\odot}$.
* **Week 11:** Evaluate the impact of the low-density neutron star crust on $k_2$ vs. $\Lambda$ by comparing core-only models against full core-plus-crust models.
* **Week 12:** Analyze EoS-insensitive quasi-universal relations ($C\text{--}\Lambda$ plane), fitting polynomial curves and quantifying maximum percentage deviations across the EoS ensemble.

### Month 4: Gravitational-Wave Constraints & Thesis Writing
* **Week 13:** Retrieve public LIGO/Virgo parameter estimation posterior samples for **GW170817** (via GWOSC). Compute the binary tidal deformability $\tilde{\Lambda}(m_1, m_2)$ along the fixed chirp-mass curve $\mathcal{M} = 1.186\,M_{\odot}$.
* **Week 14:** Generate publication-quality figures overlaying theoretical $\tilde{\Lambda}$ predictions against GW170817 observational bounds. Draft Chapters 1–3 of the thesis (Introduction, Perturbation Theory, Numerical Methods).
* **Week 15:** Draft Chapters 4–5 (Results, Universal Relations, Gravitational-Wave Constraints, and Conclusions). Clean, document, and finalize the `pyTidalNS` GitHub repository.
* **Week 16:** Advisor feedback integration, thorough proofreading, LaTeX typesetting polish, final thesis submission, and defense presentation rehearsal.

---

## 6. References

1. **Love, A. E. H.** (1909). *The Yielding of the Earth to Disturbing Forces*. Proceedings of the Royal Society of London. Series A, 82(551), 73–88.
2. **Flanagan, É. É., & Hinderer, T.** (2008). *Constraining neutron-star tidal Love numbers with gravitational-wave detectors*. Physical Review D, 77(2), 021502(R).
3. **Hinderer, T.** (2008). *Tidal Love Numbers of Neutron Stars*. The Astrophysical Journal, 677(2), 1216–1220.
4. **Binnington, T., & Poisson, E.** (2009). *Relativistic theory of tidal Love numbers*. Physical Review D, 80(8), 084018.
5. **Damour, T., & Nagar, A.** (2009). *Relativistic tidal properties of neutron stars*. Physical Review D, 80(8), 084035.
6. **Hinderer, T., Lackey, B. D., Lang, R. N., & Read, J. S.** (2010). *Tidal deformability of neutron stars with realistic equations of state and their gravitational wave signatures in binary inspiral*. Physical Review D, 81(12), 123016.
7. **Postnikov, S., Prakash, M., & Lattimer, J. M.** (2010). *Tidal Love numbers of neutron and self-bound quark stars*. Physical Review D, 82(2), 024016.
8. **Yagi, K., & Yunes, N.** (2013). *I-Love-Q: Unexpected Universal Relations for Neutron Stars and Quark Stars*. Science, 341(6144), 365–368.
9. **Abbott, B. P., et al. (LIGO Scientific Collaboration and Virgo Collaboration)** (2017). *GW170817: Observation of Gravitational Waves from a Binary Neutron Star Inspiral*. Physical Review Letters, 119(16), 161101.
10. **Abbott, B. P., et al. (LIGO Scientific Collaboration and Virgo Collaboration)** (2018). *GW170817: Measurements of Neutron Star Radii and Equation of State*. Physical Review Letters, 121(16), 161101.
11. **Chatziioannou, K.** (2020). *Neutron-star tidal deformability and equation-of-state constraints*. General Relativity and Gravitation, 52(11), 109.