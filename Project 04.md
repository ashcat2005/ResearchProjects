Undergraduate Thesis Proposal

1. Title

General Relativistic Light Bending and Synthetic X-Ray Pulse Profiles from Rotating Hotspots on Neutron Stars

2. Scope

Thermal X-ray emission originating from localized, magnetically heated polar caps ("hotspots") on the surface of rotating millisecond pulsars encodes direct information about the stellar compactness $C = GM / (Rc^2)$. Because neutron stars possess extreme surface gravitational fields ($2GM / Rc^2 \sim 0.3\text{--}0.5$), photons emitted from the stellar surface follow strongly curved null geodesics in the exterior spacetime before reaching a distant observer. Gravitational light bending allows an observer to see well beyond the classical hemisphere—and for compactness $R < 3.52\,GM/c^2$, the entire stellar surface simultaneously—thereby suppressing the observed pulse modulation amplitude and encoding mass-to-radius ratios into the energy-resolved X-ray waveform. This physical mechanism forms the foundation of NASA's Neutron Star Interior Composition Explorer (NICER) mission.

This undergraduate thesis focuses on forward-modeling synthetic X-ray light curves (pulse profiles) from rotating thermal hotspots in a static Schwarzschild exterior spacetime:

$$ds^2 = -\left(1 - \frac{2GM}{rc^2}\right)c^2\,dt^2 + \left(1 - \frac{2GM}{rc^2}\right)^{-1}dr^2 + r^2\left(d\theta^2 + \sin^2\theta\,d\phi^2\right)$$

While the gravitational field is modeled via the spherically symmetric Schwarzschild metric, the rotational kinematics of the emitting plasma on the stellar surface are incorporated via exact special-relativistic Doppler boosting, aberration of angles, and photon travel-time delays (the classic Schwarzschild + Doppler approximation).

The scope encompasses three progressive modeling stages:

1. Relativistic Photon Ray Tracing: Computing exact photon bending angles $\psi(\alpha)$ as functions of local emission angle $\alpha$ via numerical quadrature of the Schwarzschild null geodesic integral, and benchmarking accuracy against Beloborodov's analytical cosine relation ($\cos\alpha \approx 1 - (1 - \cos\psi)(1 - 2GM/Rc^2)$).

2. Infinitesimal & Finite Circular Hotspots: Integrating specific intensity $I_\nu / \nu^3 = \text{const}$ over discretized, finite-radius circular thermal caps (accounting for gravitational redshift $1+z$, Lorentz Doppler factor $\delta$, and limb-darkening laws) for single, antipodal, and non-antipodal hotspot geometries.

3. Parameter-Space & Observational Benchmarking: Quantifying how stellar compactness ($M/R$), spin frequency ($f$), observer inclination ($i$), and spot colatitude ($\theta_s$) govern pulse morphology, harmonic content, and fractional modulation amplitude, comparing synthetic waveforms against public NICER phase-folded pulse profiles (e.g., PSR J0030+0451).

Rotational oblateness of the stellar surface (the Oblate Schwarzschild approximation), Lense–Thirring frame dragging in Kerr/Hartle–Thorne spacetimes, and non-thermal magnetospheric cyclotron scattering lie outside the scope of this project.

3. Objectives

General Objective

To develop, validate, and apply a general relativistic ray-tracing and radiative-transfer code in Python to simulate energy-resolved X-ray pulse profiles from rotating neutron star hotspots, quantifying the dependence of pulse modulation and harmonic structure on stellar compactness and emission geometry.

Specific Objectives

1. Schwarzschild Geodesic Solver & Approximation Benchmarking: Implement a numerical integrator in Python (SciPy quadrature / elliptic integrals) to solve the exact photon trajectory equation relating emission angle $\alpha$ to observer deflection angle $\psi$, quantifying the fractional error of Beloborodov's analytical formula across compactness values $C \in [0.05, 0.35]$.

2. Relativistic Radiative Transfer Implementation: Formulate the observed monochromatic and bolometric flux from a rotating surface element by combining gravitational redshift $(1 + z)^{-1} = \sqrt{1 - 2C}$, special-relativistic Doppler factor $\delta = [\gamma(1 - \beta \cos\xi)]^{-1}$, lensing magnification factor $d\cos\alpha / d\cos\psi$, and photon propagation time delays $\Delta t(\psi)$.

3. Finite Hotspot Discretization: Extend the point-source solver to finite circular hotspots of angular radius $\rho_s$ by partitioning the spherical cap into an equal-area mesh, handling partial eclipses across the relativistic visibility horizon ($\alpha \le \pi/2$), and testing isotropic blackbody vs. Hopf-like atmospheric beaming functions.

4. Compactness & Geometric Degeneracy Analysis: Perform systematic parameter sweeps across compactness $C$, spin frequency $f \in [100, 700]\text{ Hz}$, inclination $i$, and spot colatitude $\theta_s$ to map fractional pulse amplitude ($A_{\text{pulse}}$) and Fourier harmonic ratios ($a_2 / a_1$), isolating the asymmetry induced by Doppler boosting.

5. Observational Comparison with NICER Data: Retrieve public phase-folded X-ray pulse profile data for PSR J0030+0451 and evaluate qualitative waveform characteristics (asymmetric rise/decay times and non-zero minimum flux), illustrating how off-center vs. antipodal hot regions reproduce observed pulse shapes.

4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. Open-Source Software Package (pyPulseRay):

	⚬ A clean, modular Python package built with NumPy, SciPy, and Matplotlib.

	⚬ Core modules for exact Schwarzschild null-geodesic integration, lookup-table interpolation for $\alpha(\psi)$ and lensing factors, Doppler-boosted blackbody/atmospheric spectrum calculators, and spherical-cap mesh generators.

	⚬ Automated unit tests verifying energy conservation, Newtonian flat-spacetime limits ($C \to 0$), and visibility boundary conditions ($\alpha = \pi/2$), paired with reproducible Jupyter notebooks generating all thesis figures.

2. Scientific Visualization & Data Suite:

	⚬ Photon trajectory plots in Schwarzschild coordinates illustrating light bending, critical impact parameters, and visibility of the far hemisphere beyond $\psi = \pi/2$.

	⚬ Diagnostic comparisons of exact geodesic bending vs. Beloborodov's approximation across varying compactness regimes.

	⚬ Energy-resolved and bolometric synthetic X-ray light curves contrasting Newtonian vs. relativistic stars, single vs. antipodal hotspots, and slow vs. millisecond spin rates, alongside contour maps of pulsed fraction in the $(i, \theta_s)$ plane.

3. Undergraduate Thesis Manuscript & Defense:

	⚬ A formal LaTeX-typeset undergraduate thesis (40–60 pages) covering general relativistic null geodesics, Lorentz transformations of specific intensity, numerical integration methods, parameter studies, and astrophysical applications to X-ray pulsars.

	⚬ A 20-minute oral defense presentation summarizing the physical theory, computational workflow, and key findings.

5. 4 Months Timeline

The project is organized across 16 weeks (4 months) into four structured monthly phases with concrete weekly milestones:

Month 1: Schwarzschild Null Geodesics & Light Bending

⚬ Week 1: Literature review of relativistic pulse-profile modeling (Pechenick, Ftaclas, & Cohen 1983; Beloborodov 2002; Poutanen & Gierliński 2003). Review the Schwarzschild exterior metric, conserved photon energy and angular momentum, and the effective potential for null geodesics.

⚬ Week 2: Derive the integral expression for the photon deflection angle $\psi(\alpha)$ from the stellar radius $R$ to infinity, identifying the maximum visible colatitude $\psi_{\text{max}}$ corresponding to tangential emission ($\alpha = \pi/2$).

⚬ Week 3: Implement the exact numerical geodesic integrator in Python (scipy.integrate.quad), handling the integrable square-root singularity near $\alpha = \pi/2$ via variable substitution.

⚬ Week 4: Code Beloborodov's analytical approximation and evaluate its relative error in both $\alpha(\psi)$ and the lensing derivative $d\cos\alpha / d\cos\psi$ across compactness parameters $C \in [0.05, 0.35]$.

Month 2: Relativistic Radiation Transport & Point-Like Hotspots

⚬ Week 5: Derive the complete flux formula for an infinitesimal rotating surface element, incorporating gravitational redshift $(1 + z)$, relativistic surface velocity $\beta = (2\pi f R / c)(1 - 2C)^{-1/2}\sin\theta_s$, Lorentz factor $\gamma$, and Doppler boosting $\delta$.

⚬ Week 6: Implement photon propagation time delays $\Delta t(\psi)$ along curved null geodesics relative to a radial photon, quantifying phase-lag distortions at millisecond spin frequencies ($f \ge 300\text{ Hz}$).

⚬ Week 7: Build the single-point-hotspot pulse-profile generator in Python. Verify code behavior in the flat-spacetime Newtonian limit ($C \to 0, \beta \to 0$), reproducing exact analytical sinusoidal light curves.

⚬ Week 8: Generate comparative light curves across energy bands ($0.3\text{--}2.0\text{ keV}$), demonstrating how Doppler boosting creates asymmetric pulse profiles (faster rise than decay) and energy-dependent phase shifts.

Month 3: Finite Circular Hotspots & Parameter Space Exploration

⚬ Week 9: Implement a spherical-cap discretization scheme to model finite circular hotspots of angular radius $\rho_s \in [5^\circ, 30^\circ]$, dividing each cap into equal-solid-angle surface elements with individual local viewing angles $\psi_k(\phi)$ and velocities $\beta_k$.

⚬ Week 10: Incorporate atmospheric beaming/limb-darkening laws $I(\alpha) \propto 1 + h\cos\alpha$ alongside isotropic blackbody emission, evaluating how anisotropic radiation alters pulse sharpness and harmonic ratios.

⚬ Week 11: Extend the simulation to two-hotspot configurations, comparing symmetric antipodal polar caps ($\theta_2 = \pi - \theta_1, \Delta\phi = \pi$) against offset, non-antipodal geometries.

⚬ Week 12: Conduct systematic parameter sweeps over $(C, i, \theta_s, f)$ to produce contour maps of fractional pulse amplitude and Fourier power ratios ($P_2 / P_1$), demonstrating how compactness suppresses modulation amplitude.

Month 4: NICER Benchmarking & Thesis Writing

⚬ Week 13: Download public NICER folded pulse-profile data for PSR J0030+0451 (via Zenodo / HEASARC) and perform qualitative comparisons with synthetic dual-hotspot waveforms to illustrate non-antipodal magnetic field signatures.

⚬ Week 14: Produce publication-grade thesis figures (ray trajectories, Beloborodov error curves, energy-resolved light curves, and pulsed-fraction heatmaps). Draft Chapters 1–3 of the thesis (Introduction, Relativistic Optics Theory, Numerical Methodology).

⚬ Week 15: Draft Chapters 4–5 (Results, Parameter Degeneracies, Observational Implications, and Conclusions). Clean, document, and finalize the pyPulseRay GitHub repository.

⚬ Week 16: Advisor review, feedback integration, LaTeX formatting polish, final thesis submission, and rehearsal of the 20-minute defense presentation.

6. References

1. Pechenick, K. R., Ftaclas, C., & Cohen, J. M. (1983). Hot spots on neutron stars: the near-field gravitational lens. The Astrophysical Journal, 274, 846–857.

2. Misner, C. W., Thorne, K. S., & Wheeler, J. A. (1973). Gravitation. W. H. Freeman and Company. (Chapter 25: Orbits of Particles and Photons in Schwarzschild Geometry).

3. Miller, M. C., & Lamb, F. K. (1998). Bounds on the Compactness of Neutron Stars from Brightness Oscillations during X-Ray Bursts. The Astrophysical Journal Letters, 499(1), L37–L40.

4. Beloborodov, A. M. (2002). Gravitational Bending of Light Near Compact Objects. The Astrophysical Journal Letters, 566(2), L85–L88.

5. Poutanen, J., & Gierliński, M. (2003). On the nature of the X-ray emission from the accreting millisecond pulsar SAX J1808.4$-$3658. Monthly Notices of the Royal Astronomical Society, 343(4), 1301–1311.

6. Poutanen, J., & Beloborodov, A. M. (2006). Pulse profiles of millisecond pulsars and their Fourier amplitudes. Monthly Notices of the Royal Astronomical Society, 373(2), 836–844.

7. Cadeau, C., Morsink, S. M., Leahy, D., & Campbell, S. S. (2007). Light Curves for Rapidly Rotating Neutron Stars. The Astrophysical Journal, 654(1), 458–469.

8. Morsink, S. M., Leahy, D. A., Cadeau, C., & Braga, J. (2007). The Oblate Schwarzschild Approximation for Light Curves of Rapidly Rotating Neutron Stars. The Astrophysical Journal, 663(2), 1244–1251.

9. Bogdanov, S., et al. (2019). Constraining the Neutron Star Mass–Radius Relation and Dense Matter Equation of State with NICER. II. Emission from Hot Spots on a Rapidly Rotating Neutron Star. The Astrophysical Journal Letters, 887(1), L26.

10. Riley, T. E., et al. (2019). A NICER View of PSR J0030+0451: Millisecond Pulsar Parameter Estimation. The Astrophysical Journal Letters, 887(1), L21.

11. Miller, M. C., et al. (2019). PSR J0030+0451 Mass and Radius from NICER Data and Implications for the Properties of Neutron Star Matter. The Astrophysical Journal Letters, 887(1), L24.
