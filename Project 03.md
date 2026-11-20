Undergraduate Thesis Proposal

1. Title

Structure, Frame Dragging, and Quadrupole Moments of Slowly Rotating Neutron Stars in the Hartle–Thorne Formalism

2. Scope

Observed neutron stars—particularly millisecond pulsars such as PSR J1748$-$2446ad (spinning at $716\text{ Hz}$)—rotate at relativistic speeds where centrifugal forces and general relativistic frame dragging significantly alter their internal structure and exterior spacetime geometry. While fully non-linear, rapidly rotating stellar configurations require solving coupled partial differential equations in two dimensions, the vast majority of known pulsars rotate well below their Keplerian mass-shedding frequency ($\Omega \ll \Omega_K$). In this regime, rotation can be treated as a small perturbation upon a static, spherically symmetric background star.

This undergraduate thesis focuses on modeling uniformly and slowly rotating, cold ($T = 0$), unmagnetized neutron stars using the perturbative Hartle–Thorne formalism, expanding the Einstein field equations and hydrostatic equilibrium conditions to second order in the stellar angular velocity $\Omega$:

$$ds^2 = -e^{2\Phi(r)}\left[1 + 2\left(h_0(r) + h_2(r)P_2(\cos\theta)\right)\right]c^2\,dt^2 + \frac{1 + 2\left(m_0(r) + m_2(r)P_2(\cos\theta)\right)/(r - 2Gm(r)/c^2)}{1 - 2Gm(r)/(rc^2)}\,dr^2 + r^2\left[1 + 2\left(v_2(r) - h_2(r)\right)P_2(\cos\theta)\right]\left[d\theta^2 + \sin^2\theta\left(d\phi - \omega(r)\,dt\right)^2\right]$$

The scope encompasses three progressive modeling stages:

1. Zeroth- and First-Order Perturbations ($O(\Omega^0)$ and $O(\Omega^1)$): Solving the background Tolman–Oppenheimer–Volkoff (TOV) equations alongside the first-order off-diagonal metric equation for the Lense–Thirring frame-dragging angular velocity $\omega(r)$, extracting the relativistic moment of inertia $I$ and total angular momentum $J$.

2. Second-Order Spherical and Quadrupolar Deformations ($O(\Omega^2)$): Integrating the $l = 0$ monopole perturbation equations to obtain rotational mass shifts ($\delta M$) and mean radius changes ($\delta R$), and solving the coupled $l = 2$ quadrupole boundary-value problem to extract the mass quadrupole moment $Q$, rotational ellipticity $e$, and Kerr-like parameter $\bar{q} = -Q c^2 / (G^2 M^3 \chi^2)$.

3. Equation of State (EoS) & Universal Relations Benchmarking: Applying the solver across relativistic polytropes and realistic tabulated nuclear EoSs (SLy4, APR4, DD2) to quantify deviations from Newtonian rotational theory (Chandrasekhar's slow-rotation approximation) and test the Equation-of-State-insensitive $I\text{--}Q$ universal relation.

Differential rotation, magnetic dipole deformations, gravitational-wave radiation reaction (CFS instability), and rapid rotation near the mass-shedding limit where $O(\Omega^3)$ and $l \ge 4$ multipoles become non-negligible lie outside the scope of this project.

3. Objectives

General Objective

To formulate, implement, and validate a modular numerical solver in Python for the Hartle–Thorne slow-rotation equations in General Relativity, characterizing how stellar rotation modifies neutron star mass, radius, frame dragging, moment of inertia, and quadrupole moment across candidate nuclear Equations of State.

Specific Objectives

1. First-Order Frame-Dragging Solver: Couple the second-order ordinary differential equation for the local inertial frame-dragging rate $\bar{\omega}(r) = \Omega - \omega(r)$ to a validated TOV solver, enforcing regularity at $r = 0$ and asymptotic matching at the stellar surface $r = R$ to compute the relativistic moment of inertia $I(M)$ and central frame-dragging ratio $\omega(0)/\Omega$.

2. Second-Order Monopole & Quadrupole Integration: Implement the $l = 0$ perturbation integrator for rotational mass and pressure corrections ($\delta m_0, \delta p_0$) and solve the inhomogeneous $l = 2$ quadrupole system ($h_2, v_2$) via linear superposition of homogeneous and particular solutions matched smoothly to the exterior Hartle–Thorne vacuum metric.

3. Analytical & Newtonian Validation: Verify code accuracy against exact analytical solutions for a slowly rotating incompressible constant-density sphere (Kerr-limit expansion and Chandrasekhar's Newtonian Maclaurin spheroid limit as compactness $C \to 0$).

4. Realistic Nuclear EoS Exploration: Compute sequences of rotating stellar configurations along constant central density ($\rho_c$) and constant baryon mass ($M_b$) evolutionary tracks for tabulated nuclear EoSs (SLy4, APR4, DD2), determining rotational mass increases ($\delta M / M_0$), polar-to-equatorial radius ratios ($R_p / R_e$), and approximate Keplerian frequency limits.

5. Testing the $I\text{--}Q$ Quasi-Universal Relation: Compute dimensionless moment of inertia $\bar{I} = c^4 I / (G^2 M^3)$ and dimensionless quadrupole moment $\bar{Q} = -c^2 Q / (G^2 M^3 \chi^2)$ across all EoSs to verify the EoS-independent Yagi–Yunes $I\text{--}Q$ relation to within $\sim 1\%$ accuracy.

4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. Open-Source Software Package (pyHartleThorne):

	⚬ A clean, modular Python codebase built with NumPy, SciPy, and Matplotlib.

	⚬ Solvers for the $O(\Omega^0)$ TOV background, $O(\Omega^1)$ frame-dragging shooting/rescaling solver, $O(\Omega^2, l=0)$ monopole solver, and $O(\Omega^2, l=2)$ quadrupole linear-superposition boundary-value solver.

	⚬ Automated EoS handlers supporting polytropes, incompressible fluids, and log-log cubic spline interpolation of tabulated nuclear EoSs (including surface density-jump junction conditions).

	⚬ Unit test suite verifying convergence order and analytical limits, paired with reproducible Jupyter notebooks generating all thesis plots.

2. Scientific Visualization & Data Suite:

	⚬ Radial internal profiles of the frame-dragging frequency $\omega(r)/\Omega$, monopole mass perturbation $m_0(r)$, and quadrupole metric functions $h_2(r)$ and $v_2(r)$.

	⚬ Relativistic vs. Newtonian comparisons of dimensionless moment of inertia $I / (M R^2)$ and rotational eccentricity $e$ as functions of compactness $C = GM / (Rc^2)$.

	⚬ Constant-baryon-mass rotational tracks on the $M\text{--}R_e$ diagram and validation plots of the $\bar{I}\text{--}\bar{Q}$ universal relation across soft and stiff nuclear EoSs.

3. Undergraduate Thesis Manuscript & Defense:

	⚬ A formal LaTeX-typeset undergraduate thesis (40–60 pages) presenting the perturbative derivation, numerical shooting/matching algorithms, code benchmarks, physical results, and pulsar astrophysics implications.

	⚬ A 20-minute oral defense presentation summarizing the methodology, numerical verification, and scientific conclusions.

5. 4 Months Timeline

The project is structured across 16 weeks (4 months) into four distinct monthly phases with concrete weekly milestones:

Month 1: Perturbative Theory & First-Order Frame Dragging ($O(\Omega^1)$)

⚬ Week 1: Literature review of the Hartle–Thorne formalism (Hartle 1967; Hartle & Thorne 1968; Sumiyoshi et al. 1999). Review the perturbed metric ansatz, stress-energy tensor of a uniformly rotating perfect fluid, and multipole decomposition.

⚬ Week 2: Derive the $O(\Omega^1)$ frame-dragging differential equation for $\bar{\omega}(r) = \Omega - \omega(r)$ and its exterior analytical vacuum solution $\bar{\omega}_{\text{ext}}(r) = \Omega - 2GJ / (c^2 r^3)$.

⚬ Week 3: Implement the baseline dimensionless TOV solver and couple the $\bar{\omega}(r)$ integrator in Python (RK4 / RK45), utilizing linearity to rescale arbitrary central guesses $\bar{\omega}_c$ to match a target spin frequency $\Omega$.

⚬ Week 4: Compute relativistic moments of inertia $I = J / \Omega$ and central frame-dragging rates $\omega(0)/\Omega$ for relativistic polytropes, comparing results against Newtonian moments of inertia.

Month 2: Second-Order Monopole & Quadrupole Perturbations ($O(\Omega^2)$)

⚬ Week 5: Derive and implement the $O(\Omega^2, l = 0)$ spherical perturbation equations for monopole mass perturbation $m_0(r)$ and pressure perturbation $p_0^*(r)$, extracting rotational mass shift $\delta M$ and mean radius shift $\delta R$.

⚬ Week 6: Formulate the coupled $O(\Omega^2, l = 2)$ quadrupole ODE system for $h_2(r)$ and $v_2(r)$, including the algebraic relation for quadrupole pressure perturbation $p_2^*(r)$ and exterior associated Legendre functions ($Q_2^2$).

⚬ Week 7: Implement the linear superposition boundary-value solver (integrating one inhomogeneous particular solution plus one homogeneous solution from $r \to 0$ and matching $h_2, v_2$ continuously at $r = R$) to extract the quadrupole moment $Q$.

⚬ Week 8: Validate the full $O(\Omega^2)$ code against analytical slow-rotation results for an incompressible constant-density fluid sphere (including surface density-discontinuity corrections) and Chandrasekhar's Newtonian Maclaurin spheroid limit ($e^2 = \frac{15}{4} \frac{\Omega^2}{2\pi G \rho}$).

Month 3: Realistic Nuclear EoSs & Universal Relations

⚬ Week 9: Acquire tabulated microphysical nuclear EoSs (SLy4, APR4, DD2) from public repositories (CompOSE). Implement thermodynamically consistent cubic spline interpolation and verify smooth derivatives across the core–crust transition.

⚬ Week 10: Compute rotating neutron star sequences across stable central densities at fixed spin frequencies (e.g., $f = 300\text{ Hz}$ and $716\text{ Hz}$, matching PSR J1748$-$2446ad), quantifying $\delta M / M_0$, equatorial vs. polar radii ($R_e, R_p$), and surface redshift corrections.

⚬ Week 11: Construct constant-baryon-mass ($M_b = \text{const}$) spin-down evolutionary sequences to model how an isolated pulsar contracts and spins down as it loses rotational kinetic energy.

⚬ Week 12: Evaluate dimensionless $\bar{I}$ and $\bar{Q}$ across all tabulated EoSs and polytropes to test the Yagi–Yunes $\bar{I}\text{--}\bar{Q}$ universal relation, quantifying maximum fractional deviations across the EoS ensemble.

Month 4: Astrophysical Synthesis & Thesis Writing

⚬ Week 13: Assess the validity regime of the slow-rotation approximation by comparing rotational kinetic-to-gravitational energy ratios ($T/\vert{}W\vert{}$) and estimating Keplerian breakup limits ($\Omega_K$) across EoSs.

⚬ Week 14: Generate publication-grade thesis figures (radial perturbation profiles, $I(M)$ curves, $M\text{--}R_e$ rotational shifts, and $\bar{I}\text{--}\bar{Q}$ universality plots). Draft Chapters 1–3 of the thesis (Introduction, Hartle–Thorne Theory, Numerical Methods).

⚬ Week 15: Draft Chapters 4–5 (Code Validation, Nuclear EoS Results, Universal Relations, and Conclusions). Clean, document, and finalize the pyHartleThorne GitHub repository.

⚬ Week 16: Advisor review, feedback integration, LaTeX typesetting polish, final thesis submission, and rehearsal of the 20-minute defense presentation.

6. References

1. Chandrasekhar, S. (1933). The Equilibrium of Distorted Polytropes. I. The Rotational Problem. Monthly Notices of the Royal Astronomical Society, 93(5), 390–406.

2. Hartle, J. B. (1967). Slowly Rotating Relativistic Stars. I. Equations of Structure. The Astrophysical Journal, 150, 1005–1029.

3. Hartle, J. B., & Thorne, K. S. (1968). Slowly Rotating Relativistic Stars. II. Models for Neutron Stars and Supermassive Stars. The Astrophysical Journal, 153, 807–834.

4. Chandraskhar, S., & Miller, J. C. (1974). On Slowly Rotating Homogeneous Masses in General Relativity. Monthly Notices of the Royal Astronomical Society, 167(1), 63–79.

5. Weber, F., & Glendenning, N. K. (1992). Application of the Improved Hartle Method for the Construction of General Relativistic Rotating Neutron Star Models. The Astrophysical Journal, 390, 541–549.

6. Berti, E., White, F., Maniopoulou, A., & Bruni, M. (2005). Rotating neutron stars: an invariant comparison of approximate and numerical spacetime models. Monthly Notices of the Royal Astronomical Society, 358(3), 923–938.

7. Hessels, J. W. T., et al. (2006). A Radio Pulsar Spinning at 716 Hz. Science, 311(5769), 1901–1904.

8. Yagi, K., & Yunes, N. (2013). I-Love-Q: Unexpected Universal Relations for Neutron Stars and Quark Stars. Science, 341(6144), 365–368.

9. Paschalidis, V., & Stergioulas, N. (2017). Rotating stars in relativity. Living Reviews in Relativity, 20(1), 7.

10. Urbec, M., & Miller, J. C. (2019). Slowly rotating relativistic stars: interior and exterior matching. Classical and Quantum Gravity, 36(14), 145005.
