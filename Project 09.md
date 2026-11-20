Undergraduate Thesis Proposal

1. Title

Solving the Relativistic Tolman–Oppenheimer–Volkoff Equations Using Physics-Informed Neural Networks (PINNs)

2. Scope

Determining the internal structure and Mass–Radius ($M\text{--}R$) relation of neutron stars requires solving the coupled, non-linear Tolman–Oppenheimer–Volkoff (TOV) ordinary differential equations of general relativistic hydrostatic equilibrium alongside a dense-matter Equation of State (EoS), $P(\epsilon)$. Traditional numerical solvers—such as 4th-order Runge–Kutta (RK4) or adaptive shooting algorithms—integrate outward on discrete radial grids for a single central pressure $P_c$ at a time. When generating thousands of stellar configurations for Bayesian multi-messenger inference or exploring high-dimensional EoS parameter spaces, repeated sequential grid integrations can become computationally expensive and lack analytical differentiability with respect to input parameters.

Physics-Informed Neural Networks (PINNs) (Raissi, Perdikaris, & Karniadakis 2019) offer a mesh-free, differentiable scientific machine learning paradigm. Rather than learning purely from pre-computed labeled datasets, a PINN embeds the governing differential equations, initial conditions at the stellar center ($r = 0$), and surface boundary conditions ($P(R) = 0$) directly into the neural network's composite loss function via automatic differentiation:

$$\mathcal{L}_{\text{total}} = w_{\text{ODE}}\,\mathcal{L}_{\text{TOV}} + w_{\text{BC}}\,\mathcal{L}_{\text{center/surface}} + w_{\text{phys}}\,\mathcal{L}_{\text{positivity}}$$

Once trained across a continuous domain of radial coordinates and central densities $(r, \rho_c)$, the network acts as a fast, smooth, and infinitely differentiable surrogate solver capable of predicting internal radial profiles and global stellar observables $(M, R)$ in a single forward pass.

This undergraduate thesis focuses on formulating, training, and benchmarking PINN architectures in TensorFlow to solve the static, spherically symmetric TOV equations. The scope encompasses three progressive modeling stages:

1. Single-Star PINN Solver & Hard Boundary Enforcement: Reformulating the dimensionless TOV system on a normalized radial domain $\xi = r / R \in [0, 1]$ (treating the unknown stellar radius $R$ as a trainable scalar parameter) and enforcing exact central boundary conditions ($m(0) = 0$, $P(0) = P_c$) and surface conditions ($P(R) = 0$) via hard-constrained ansatz trial functions.

2. Parametric Continuous-Family PINNs: Extending the network inputs to $( \xi, \log \rho_c )$ and EoS stiffness parameters (polytropic index $\Gamma$ and constant $K$) so a single trained network simultaneously learns an entire continuous family of neutron star interiors and the complete $M\text{--}R$ curve.

3. Numerical Benchmarking & Realistic Nuclear EoS Extension: Quantitatively evaluating solution accuracy ($L_2$ and $L_\infty$ relative errors), training convergence, and batch inference speed against a high-precision RK4 reference solver across relativistic polytropes, the analytical constant-density Schwarzschild sphere, and piecewise-polytropic approximations of realistic nuclear EoSs (SLy4 and APR4).

Non-static 3D general relativistic magnetohydrodynamics (GRMHD), rotating Hartle–Thorne spacetimes, and direct Bayesian parameter estimation on raw gravitational-wave strain data lie outside the scope of this project.

3. Objectives

General Objective

To design, implement, and rigorously benchmark a Physics-Informed Neural Network framework in TensorFlow for solving the coupled Tolman–Oppenheimer–Volkoff equations, evaluating its numerical accuracy, parameter-space interpolation capability, and computational efficiency relative to classical Runge–Kutta integrators.

Specific Objectives

1. Dimensionless Free-Boundary PINN Formulation: Reformulate the coupled TOV differential equations onto a fixed normalized radial coordinate $\xi = r / R \in [0, 1]$ so the unknown stellar radius $R$ becomes an explicit trainable variable, eliminating the moving-boundary stiffness common in standard neural ODE solvers.

2. Hard-Constrained Trial Function Architecture: Construct smooth multilayer perceptron (MLP) architectures in TensorFlow (tf.GradientTape) using analytical ansatz transformations that identically satisfy central regularity ($m(0) = 0$, $dP/dr\vert{}_{r=0} = 0$) and surface pressure vanishing ($P(\xi = 1) = 0$), removing competing boundary-loss weight hyper-parameters.

3. Analytical & RK4 Accuracy Benchmarking: Validate single-star PINN predictions of pressure $P(r)$, enclosed mass $m(r)$, total gravitational mass $M$, and stellar radius $R$ against the exact analytical constant-density Schwarzschild interior solution and a high-precision RK4 solver across relativistic polytropes ($\Gamma \in [1.5, 2.5]$), targeting $< 10^{-3}$ relative error.

4. Parametric Multi-Star & EoS Generalization: Train a parametric PINN conditioned on central density $\rho_c$ and polytropic EoS parameters $(K, \Gamma)$, plus piecewise-polytropic fits to realistic nuclear EoSs (SLy4, APR4), to generate continuous $M\text{--}R$ curves and evaluate out-of-sample interpolation accuracy.

5. Computational Performance & Stability Diagnostics: Quantify training wall-clock time, optimizer behavior (Adam pre-training followed by L-BFGS second-order fine-tuning), collocation point sampling strategies (uniform vs. Latin Hypercube / residual-based adaptive refinement), and vectorized inference speedups compared to sequential RK4 integration.

4. Deliverable

At the conclusion of the 4-month research period, the student will deliver the following artifacts:

1. Open-Source Software Package (pyPINN-TOV):

	⚬ A clean, modular, PEP-8 compliant Python codebase built on TensorFlow 2.x, NumPy, SciPy, and Matplotlib.

	⚬ Core modules implementing dimensionless TOV residuals via nested tf.GradientTape automatic differentiation, hard-constrained neural network trial layers, hybrid Adam + L-BFGS training loops, and a reference RK4 solver for ground-truth benchmarking.

	⚬ Automated unit tests verifying automatic differentiation gradients, exact satisfaction of boundary conditions, and analytical incompressible-sphere recovery, paired with reproducible Jupyter notebooks generating all thesis figures.

2. Scientific Visualization & Data Suite:

	⚬ Loss-convergence trajectories (PDE residual loss vs. epoch) comparing soft boundary penalties against hard-constrained trial functions and Adam vs. Adam+L-BFGS optimization.

	⚬ Radial profile comparisons ($P(r)$, $m(r)$, and pointwise absolute/relative error distributions) contrasting PINN predictions against RK4 solutions for canonical $1.4\,M_{\odot}$ and maximum-mass stars.

	⚬ Continuous $M\text{--}R$ curves predicted by the parametric PINN across relativistic polytropes and piecewise-polytropic nuclear EoSs (SLy4, APR4), accompanied by inference-time scaling benchmarks.

3. Undergraduate Thesis Manuscript & Defense:

	⚬ A formal LaTeX-typeset undergraduate thesis (40–60 pages) covering relativistic stellar structure theory, physics-informed deep learning mathematics, neural architecture and optimization design, quantitative error benchmarks, and computational astrophysics discussion.

	⚬ A 20-minute oral defense presentation summarizing the theoretical formulation, neural network methodology, benchmark results, and conclusions.

5. 4 Months Timeline

The project is organized across 16 weeks (4 months) into four structured monthly phases with concrete weekly milestones:

Month 1: Relativistic Stellar Structure & Reference RK4 Solver

⚬ Week 1: Literature review of the TOV equations (Oppenheimer & Volkoff 1939; Shapiro & Teukolsky 1983) and Physics-Informed Neural Networks for differential equations (Raissi et al. 2019; Lagaris et al. 1998; Cuomo et al. 2022).

⚬ Week 2: Derive the dimensionless TOV system and formulate the coordinate transformation $\xi = r / R \in [0, 1]$ that maps the free-boundary problem onto a fixed domain with trainable radius $R$.

⚬ Week 3: Implement and validate a high-precision reference RK4 TOV solver in Python (NumPy/SciPy) for incompressible spheres, relativistic polytropes, and piecewise-polytropic EoSs (Read et al. 2009).

⚬ Week 4: Set up the TensorFlow 2.x GPU/CPU development environment and build a prototype single-ODE PINN (solving the Newtonian Lane–Emden equation) to verify tf.GradientTape derivative accuracy and baseline training workflows.

Month 2: Single-Star TOV PINN & Hard Boundary Constraints

⚬ Week 5: Implement the coupled TOV physics-informed loss function in TensorFlow, enforcing non-negativity of pressure and mass ($P \ge 0, m \ge 0$) and avoiding coordinate singularities near $\xi \to 0$.

⚬ Week 6: Design and test hard-constrained trial functions ($m(\xi) = \xi^3 \hat{m}(\xi)$ and $P(\xi) = P_c (1 - \xi^2)\hat{P}(\xi)$) that automatically satisfy exact central and surface boundary conditions without manual loss-weight tuning.

⚬ Week 7: Implement a two-stage optimization pipeline combining Adam first-order stochastic optimization with L-BFGS quasi-Newton fine-tuning (scipy.optimize / tensorflow_probability), benchmarking convergence stability and activation functions (tanh, swish/silu, sin).

⚬ Week 8: Validate the single-star PINN against the exact analytical constant-density Schwarzschild solution and RK4 polytropic models across low-, canonical-, and high-compactness regimes, quantifying $L_2$ and $L_\infty$ relative errors.

Month 3: Parametric PINNs & Realistic Nuclear EoSs

⚬ Week 9: Extend the neural network input space to $(\xi, \log \rho_c)$ so a single parametric PINN learns continuous families of neutron star interiors across $\rho_c \in [3 \times 10^{14}, 3 \times 10^{15}]\text{ g cm}^{-3}$.

⚬ Week 10: Implement Latin Hypercube Sampling (LHS) and Residual-Based Adaptive Refinement (RAR) collocation strategies to concentrate training points in high-gradient regions near the stellar core and surface crust.

⚬ Week 11: Incorporate differentiable piecewise-polytropic representations of realistic nuclear Equations of State (SLy4 and APR4; Read et al. 2009) into the TensorFlow computational graph, training the parametric PINN to predict complete nuclear $M\text{--}R$ curves.

⚬ Week 12: Evaluate interpolation accuracy on unseen central densities and EoS parameters, identifying failure modes near the maximum-mass turning point ($\partial M / \partial \rho_c = 0$) and unstable branch.

Month 4: Computational Benchmarking & Thesis Writing

⚬ Week 13: Conduct comprehensive computational benchmarks measuring training cost vs. amortized batch inference speed ($10^3$ to $10^5$ stellar evaluations) against vectorized/sequential RK4 solvers.

⚬ Week 14: Generate publication-grade thesis figures (network architecture schematics, Adam+L-BFGS loss curves, radial profile error plots, and PINN vs. RK4 $M\text{--}R$ curves). Draft Chapters 1–3 of the thesis (Introduction, TOV Theory, PINN Methodology).

⚬ Week 15: Draft Chapters 4–5 (Benchmarking Results, Nuclear EoS Generalization, Strengths & Limitations of PINNs in Astrophysics, and Conclusions). Clean, document, and finalize the pyPINN-TOV GitHub repository.

⚬ Week 16: Advisor review, feedback integration, LaTeX typesetting polish, final thesis submission, and rehearsal of the 20-minute defense presentation.

6. References

1. Oppenheimer, J. R., & Volkoff, G. M. (1939). On Massive Neutron Cores. Physical Review, 55(4), 374–381.

2. Shapiro, S. L., & Teukolsky, S. A. (1983). Black Holes, White Dwarfs, and Neutron Stars: The Physics of Compact Objects. John Wiley & Sons.

3. Lagaris, I. E., Likas, A., & Fotiadis, D. I. (1998). Artificial neural networks for solving ordinary and partial differential equations. IEEE Transactions on Neural Networks, 9(5), 987–1000.

4. Read, J. S., Lackey, B. D., Owen, B. J., & Friedman, J. L. (2009). Constraints on a phenomenologically parameterized neutron-star equation of state. Physical Review D, 79(12), 124032.

5. Raissi, M., Perdikaris, P., & Karniadakis, G. E. (2019). Physics-informed neural networks: A deep learning framework for solving forward and inverse problems involving nonlinear partial differential equations. Journal of Computational Physics, 378, 686–707.

6. Lu, L., Meng, X., Mao, Z., & Karniadakis, G. E. (2021). DeepXDE: A Deep Learning Library for Solving Differential Equations. SIAM Review, 63(1), 208–228.

7. Cuomo, S., Di Cola, V. S., Giampaolo, F., Rozza, G., Raissi, M., & Piccialli, F. (2022). Scientific Machine Learning Through Physics–Informed Neural Networks: Where We Are and What's Next. Journal of Scientific Computing, 92(3), 88.

8. Mattheakis, M., Sondak, D., Dogra, A. S., & Protopapas, P. (2022). Hamiltonian neural networks for solving equations of motion. Physical Review E, 105(6), 065305.

9. Auddy, S., Dey, R., & Lin, M.-K. (2024). Gravitational Collapse of Relativistic Polytropes Using Physics-Informed Neural Networks. The Astrophysical Journal, 962(1), 45.

10. Toscano, J. D., Oommen, V., Varghese, A. J., Zou, Z., Daryakenari, N. A., Wu, C., & Karniadakis, G. E. (2025). From PINNs to PIKANs: recent advances in physics-informed machine learning. Machine Learning for Computational Science and Engineering, 1(1), 15.
