# Undergraduate Thesis Proposal

## 1. Title
**Mass–Radius Relations and Relativistic Stability Analysis of Neutron Stars via the Tolman–Oppenheimer–Volkoff Equations**

---

## 2. Scope
Neutron stars are the ultra-dense remnants of core-collapse supernovae, compressing roughly $1.4$ to $2.1\,M_{\odot}$ within a radius of approximately $10\text{--}13\text{ km}$. At core densities exceeding several times the nuclear saturation density ($\rho_0 \approx 2.8 \times 10^{14}\text{ g cm}^{-3}$), matter cannot be described by Newtonian gravity or standard terrestrial nuclear experiments. Instead, internal hydrostatic equilibrium requires solving Einstein's field equations of General Relativity coupled to a dense-matter Equation of State (EoS), $P(\epsilon)$, which relates pressure $P$ to total energy density $\epsilon$.

This undergraduate thesis focuses on the numerical modeling and stability analysis of **static, spherically symmetric, cold ($T = 0$), and unmagnetized neutron stars**. Within this idealized regime, spacetime is described by the static, spherically symmetric metric:

$$ds^2 = -e^{2\Phi(r)}c^2\,dt^2 + \left(1 - \frac{2Gm(r)}{rc^2}\right)^{-1}dr^2 + r^2\left(d\theta^2 + \sin^2\theta\,d\phi^2\right)$$

The project bridges analytical astrophysics, computational physics, and observational astronomy by progressing through three levels of physical realism:
1. **Analytical & Idealized Models:** Testing numerical solvers against the constant-density incompressible fluid sphere (Schwarzschild interior solution), relativistic polytropes ($P = K\rho^{\Gamma}$), and an ideal relativistic degenerate neutron Fermi gas.
2. **Realistic Nuclear Equations of State:** Incorporating tabulated microphysical EoSs derived from modern nuclear many-body theory (specifically **SLy4** and **APR4**), including crustal modeling (BPS/NV crusts) and thermodynamic consistency checks.
3. **Observational Confrontation:** Comparing theoretical Mass–Radius ($M\text{--}R$) curves directly against modern astrophysical constraints, including radio pulsar mass measurements above $2\,M_{\odot}$ and Bayesian $M\text{--}R$ posterior contours from NASA's Neutron Star Interior Composition Explorer (**NICER**).

Rotational deformation (Hartle–Thorne formalism), magnetic field stresses, and finite-temperature proto-neutron star evolution lie outside the scope of this project.

---

## 3. Objectives

### General Objective
To develop, validate, and apply a modular numerical solver in Python for the coupled Tolman–Oppenheimer–Volkoff (TOV) equations in order to map the Mass–Radius parameter space of neutron stars, determine their relativistic stability limits, and evaluate the viability of candidate nuclear Equations of State against modern observational data.

### Specific Objectives
1. **Numerical Formulation & Validation:** Nondimensionalize the coupled TOV hydrostatic equilibrium and mass-continuity differential equations, implement a 4th-order Runge–Kutta (RK4) integrator from scratch in Python, and validate numerical accuracy ($< 10^{-6}$ relative error) against the exact analytical constant-density interior Schwarzschild solution.
2. **Equation of State Implementation:** Construct an extensible EoS module supporting relativistic polytropes, exact parametric solutions for a zero-temperature relativistic degenerate neutron Fermi gas, and log-log cubic spline / piecewise polytropic interpolation for tabulated nuclear EoSs (SLy4 and APR4).
3. **Relativistic vs. Newtonian Comparison:** Quantify the impact of general relativistic corrections (pressure self-gravity, spacetime curvature factor, and gravitational binding energy) by comparing TOV stellar profiles directly against solutions of the Newtonian Lane–Emden equation.
4. **Stability & Physical Causality Analysis:** Generate sequences of stellar configurations across central densities $\rho_c \in [10^{14}, 10^{16}]\text{ g cm}^{-3}$ to identify the maximum stable mass ($M_{\text{max}}$), verify the static stability criterion ($\partial M / \partial \rho_c > 0$), check adherence to the Buchdahl compactness limit ($R > \frac{9}{4}\frac{GM}{c^2}$), and ensure subluminal adiabatic sound speeds ($c_s = \sqrt{dP/d\epsilon} \le c$).
5. **Observational Benchmarking:** Overlay theoretical $M\text{--}R$ sequences and surface gravitational redshift predictions ($z_{\text{surf}}$) onto public NICER credible contours (PSR J0030+0451 and PSR J0740+6620) and Shapiro-delay mass limits to rule out overly soft EoSs.

---

## 4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. **Open-Source Software Package (`pyTOV-NS`):**
   * A clean, modular, PEP-8 compliant Python codebase utilizing `NumPy`, `SciPy`, and `Matplotlib`.
   * Core modules for RK4 and adaptive Runge–Kutta–Fehlberg (`RK45`) integration, analytical and tabulated EoS handlers, and automated event detection for the stellar surface ($P(R) \to 0$).
   * A suite of unit tests verifying convergence order ($O(h^4)$) and thermodynamic consistency ($d\epsilon / dn = (\epsilon + P)/n$).
   * Reproducible Jupyter notebooks generating all thesis figures.

2. **Scientific Visualization & Data Suite:**
   * High-resolution plots of internal radial structure profiles ($P(r)$, $m(r)$, $\rho(r)$, and metric potential $\Phi(r)$) for canonical $1.4\,M_{\odot}$ and maximum-mass configurations.
   * Comparative $M\text{--}R$ diagrams contrasting Newtonian vs. relativistic stars, ideal Fermi gas vs. nuclear EoSs, and observational NICER 68% and 95% confidence contours.
   * Stability curves ($M$ vs. $\rho_c$ and $M$ vs. $R$) highlighting unstable branches and superluminal sound-speed regimes.

3. **Undergraduate Thesis Manuscript & Defense:**
   * A formal LaTeX-typeset undergraduate thesis (40–60 pages) covering theoretical derivations, numerical methods, code verification, physical results, and astrophysical discussion.

---

## 5. 4 Months Timeline

The project is structured across **16 weeks (4 months)**, organized into four monthly phases with concrete weekly milestones:

### Month 1: Theoretical Foundations & Core Numerical Solver
* **Week 1:** Literature review of relativistic stellar structure (Shapiro & Teukolsky; Glendenning). Derive the TOV equations from the Einstein field equations and the conservation of the stress-energy tensor ($\nabla_\mu T^{\mu\nu} = 0$).
* **Week 2:** Nondimensionalize the TOV system into geometrized/dimensionless units to prevent floating-point overflow/underflow. Handle the coordinate singularity at $r = 0$ via Taylor series expansion near the stellar center.
* **Week 3:** Implement the fixed-step RK4 integrator in Python. Implement surface boundary detection ($P(R) = P_{\text{surf}}$) and test step-size convergence.
* **Week 4:** Validate the numerical solver against the analytical incompressible fluid sphere (constant density $\rho = \rho_0$) and verify the Buchdahl limit ($2GM / Rc^2 < 8/9$).

### Month 2: Analytical Equations of State & Relativistic Effects
* **Week 5:** Implement Newtonian Lane–Emden solvers and relativistic polytropic EoSs ($P = K\rho^{\Gamma}$) for varying adiabatic indices ($\Gamma = 5/3, 2, 2.5$).
* **Week 6:** Derive and code the exact analytical parametric EoS for a cold, relativistic degenerate neutron Fermi gas. Reproduce the classic Oppenheimer–Volkoff mass limit ($M_{\text{OV}} \approx 0.71\,M_{\odot}$).
* **Week 7:** Perform systematic comparisons between Newtonian and general relativistic stellar models at identical central densities, isolating the destabilizing role of pressure as a source of gravity.
* **Week 8:** Compute gravitational binding energy ($E_b = (M_b - M)c^2$), compactness parameter ($C = GM/Rc^2$), and surface gravitational redshift ($z_{\text{surf}} = (1 - 2C)^{-1/2} - 1$).

### Month 3: Realistic Nuclear EoSs & Stability Diagnostics
* **Week 9:** Acquire tabulated nuclear EoS data (SLy4, APR4, and a soft hyperonic EoS for contrast) from public repositories (e.g., CompOSE). Implement thermodynamically consistent log-log cubic spline interpolation.
* **Week 10:** Integrate realistic low-density crustal EoSs (Baym–Pethick–Sutherland) seamlessly with high-density core tables, ensuring continuity of pressure and chemical potential.
* **Week 11:** Run parameter sweeps across central densities to generate complete $M\text{--}R$ sequences. Identify $M_{\text{max}}$, corresponding radii $R_{1.4}$ and $R_{\text{max}}$, and turning points where $\partial M / \partial \rho_c = 0$.
* **Week 12:** Compute adiabatic sound-speed profiles $c_s(\rho) = \sqrt{dP/d\epsilon}$ across all stellar interiors to flag any non-causal ($c_s > c$) behavior at extreme densities.

### Month 4: Observational Comparison & Thesis Writing
* **Week 13:** Retrieve public NICER mass–radius posterior samples for **PSR J0030+0451** and **PSR J0740+6620** (via Zenodo) and incorporate Shapiro-delay mass measurements (e.g., PSR J0348+0432).
* **Week 14:** Produce final publication-grade figures overlaying theoretical $M\text{--}R$ curves with observational contours. Draft Chapters 1–3 of the thesis (Introduction, Theoretical Framework, Numerical Methodology).
* **Week 15:** Draft Chapters 4–5 (Results, Observational Constraints, Discussion, and Conclusions). Clean, document, and finalize the GitHub code repository.
* **Week 16:** Advisor review, proofreading, LaTeX formatting polish, and final thesis submission.

---

## 6. References

1. **Tolman, R. C.** (1939). *Static Solutions of Einstein's Field Equations for Spheres of Fluid*. Physical Review, 55(4), 364–373.
2. **Oppenheimer, J. R., & Volkoff, G. M.** (1939). *On Massive Neutron Cores*. Physical Review, 55(4), 374–381.
3. **Buchdahl, H. A.** (1959). *General Relativistic Fluid Spheres*. Physical Review, 116(4), 1027–1034.
4. **Baym, G., Pethick, C., & Sutherland, P.** (1971). *The Ground State of Matter at High Densities: Equation of State and Stellar Models*. The Astrophysical Journal, 170, 299–317.
5. **Shapiro, S. L., & Teukolsky, S. A.** (1983). *Black Holes, White Dwarfs, and Neutron Stars: The Physics of Compact Objects*. John Wiley & Sons.
6. **Akmal, A., Pandharipande, V. R., & Ravenhall, D. G.** (1998). *Equation of state of nucleon matter and neutron star structure*. Physical Review C, 58(3), 1804–1828.
7. **Glendenning, N. K.** (2000). *Compact Stars: Nuclear Physics, Particle Physics, and General Relativity* (2nd ed.). Springer.
8. **Douchin, F., & Haensel, P.** (2001). *A unified equation of state of dense matter and neutron star structure*. Astronomy & Astrophysics, 380(1), 151–167.
9. **Antoniadis, J., et al.** (2013). *A Massive Pulsar in a Compact Relativistic Binary*. Science, 340(6131), 1233232.
10. **Riley, T. E., et al.** (2019). *A NICER View of PSR J0030+0451: Millisecond Pulsar Parameter Estimation*. The Astrophysical Journal Letters, 887(1), L21.
11. **Miller, M. C., et al.** (2019). *PSR J0030+0451 Mass and Radius from NICER Data and Implications for the Properties of Neutron Star Matter*. The Astrophysical Journal Letters, 887(1), L24.
12. **Miller, M. C., et al.** (2021). *The Radius of PSR J0740+6620 from NICER and XMM-Newton Data*. The Astrophysical Journal Letters, 918(2), L28.