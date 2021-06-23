---
layout: page
title: My Statistical Field Theory Notes
description: Repertoire of important formulae useful for phase transitions
img: /assets/img/mexicanhat.png
importance: 3
---

# SFT

## Key derivations/proofs/theorems:

### Chapter 1: From Spins to Fields

- Canonical ensemble: $p[s_i] = \frac{\exp[-\beta E[s_i]]}{Z}$
- Thermodynamic free-energy: $Z(T,J,B) = e^{-\beta F_{\text{thermo}}}$, $F = \langle E \rangle - TS$
- $\langle E\rangle=-\frac{\partial}{\partial \beta} \ln Z$
- Effective free-energy for spins on a lattice by introducing the order parameter m
- Saddle-point approximation to the partition function by minimizing the free energy: $Z = \Omega(m) e^{-\beta E[m]}$
- Deriving the critical temperature for the Mean-Field approximation of the Ising model
- Continuous phase transition: For no magnetic field ($B=0$), as $T \rightarrow T_c$, the order parameter (magnetization $m$) continuously transitions from a finite value to zero
- Nth order phase transition: If the free-energy is continuous up until the Nth derivative with respect to T, it is said to be an Nth order phase transition (e.g., heat capacity is discontinuous near the critical point since $m \sim \sqrt{T}$ for $T<T_c$ and $m=0$ above the critical temperature.  To find the critical exponent related for the heat capacity, just plug in the mean-field solution into the free energy and take appropriate derivatives.
- The phase diagram of the Ising model consists of a $m=0$ which corresponds to no global minima, and branch cuts which correspond the spontaneously broken $\mathbb{Z}_2$ symmetry. If we turn on the magnetic field, then there is a discontinuous phase transition below the critical temperature, and a continuous one above it.
- Draw the phase diagram for the Ising model
    - $C = \frac{\partial \langle E \rangle}{\partial T} = \beta^2 \frac{ \partial^2}{\partial \beta^2} \log Z, m_0 = \sqrt{3(T_c -T )/T}$,

    $\ln Z \approx-\beta N f\left(m_{\min }\right)$

- Derive the magnetic susceptibility of the Ising model near the critical point and derive its scaling behaviour ($\chi \sim (T-T_c)^{-\delta}$) $\chi = \frac{\partial m}{\partial B}$
- $c \sim t^{-\alpha}$, $m \sim t^\beta$, $m \sim B^{1/\delta}$, $\chi \sim t^{-\gamma}$
- Landau-Ginzburg: The free energy is a functional. Spatial fluctuations tell us the energy cost of having domain walls.
- A local, analytic, even, and translational invariant free energy has the form of $F[m(x)] = \int d^dx \left[ \frac{1}{2}\alpha_2(T) m^2 + \frac{1}{4} \alpha_4(T) m^4 + \frac{1}{2} \gamma(T) (\nabla m)^2 + \dots \right]$
- Show that $\alpha_2 \sim T-T_C, \alpha_4 \sim \tfrac{1}{3}T$ in the Ising model
- Show that there are no phase transitions in one dimension
- Lower critical dimension: any mean field theory result fails below that
- Upper critical dimension: mean field theory works above this dimension
- Show that $p[n \text{ walls}] = \frac{1}{Z n!} \left(\frac{L e^{-\beta F_{wall}}}{W}\right)^n$and that there are no phase transitions in one dimensions

### Chapter 2: Functional Integration

- $\phi(x) = \int \frac{d^d k}{(2\pi)^d}e^{ik\cdot x}\phi_k = \frac{1}{V} \sum_k e^{ik\cdot x}\phi_k$
- The UV and IR cutoffs are defined by the lattice spacing and box size: $\frac{2\pi}{L} < k < \Lambda = \frac{2\pi}{a}$
- Derive the partition function of the Gaussian free energy  $f(\phi) = \frac{1}{2}\gamma (\nabla \phi)^2 + \frac{1}{2}\mu^2 \phi^2$  in a finite box of length $L$ in $d$-dimensions.
- Explain how to compute the the heat capacity $c = \frac{\beta^2}{V}\frac{\partial^2}{\partial \beta^2} \log Z$ for the Gaussian theory
- Show that in the Gaussian theory, assuming $\mu^2 \sim T-T_c$ near the critical point, that $c\sim (T_c - T)^{-\alpha}$ has $\alpha = \frac{4-d}{2}$.
- Show that the heat capacity of the Gaussian model behaves like: $c=\frac{1}{2}\int\frac{d^dk}{(2\pi)^d}\left[1-\frac{2T}{\gamma k^2 + \mu^2(T)} + \frac{T^2}{(\gamma k^2 + \mu^2(T))^2}\right]$
- Show that $\langle \phi(x) \rangle_{B} = \frac{1}{\beta} \frac{\delta}{\delta B(x)} \log Z[B(x)]$, where $F_{\text{thermo}}[\phi] = F_0[\phi] - \int d^d x B(x)\phi(x)$
- Show that the second cumulant is given by: $\langle \phi(x) \phi(y)\rangle_{B} - \langle \phi(x)\rangle_{B}\langle \phi(y)\rangle_{B} = \frac{1}{\beta^2} \frac{\delta^2}{\delta B(x)\delta B(y)} \log Z[B(x)]$
- Show, by completing an appropriate square, that in the Gaussian theory, the partition function (up to an overall constant multiple) is given by $Z[B(x)] = Z[0]\exp{\left(\frac{\beta}{2}\int\frac{d^d k}{(2\pi)^d} \frac{B_k B_{-k}}{\gamma k^2 + \mu^2}\right)} = Z[0]\exp{\left(\frac{\beta}{2}\int d^d x d^dy B(x)G(x-y)B(y)\right)}$
- Now show that the correlation function in the absence of a magnetic field is $\langle \phi(x) \phi(y) \rangle = \frac{1}{\beta}G(x-y)$ and find the function $G(x-y)$.
- Prove the Orstein-Zernicke correlation: $G(x-y) \sim r^{2-d}, e^{-r/\zeta}r^{(1-d)/2}$ in the regimes where $r < \xi$, $r>\xi$ respectively.  Find the correlation length $\xi$.
- Verify that the correlation two-point function $G(x)$ is a Green's function to the Saddle-point approximation (i.e., solves the Euler-Lagrange equations in the presence of a source-charge).
- Show using the definition $\chi = \frac{\partial m}{\partial B}$ that $\chi(x,y) = \frac{\delta\langle \phi(x)\rangle}{\delta B(y)} = G(x,y)$ so that the coarse grained susceptibility is $\chi = \int d^d x G(x)$.
- Show that the correlation length has the following critical behaviour $\xi \sim |T-T_c|^{-\nu}$ with $\nu = 1/2$
- We write $\langle \phi(x) \phi(y) \rangle \sim r^{2-d-\eta}$. What is $\eta$ in the Mean Field Gaussian Theory? (hint)
- Show that the upper critical dimension (the lowest dimension such that Mean Field Theory holds) is governed by $\langle \phi^2 \rangle < \langle \phi \rangle^2$ (i.e., the fluctuations of the field are much smaller than the average value of the field). Show that $R = \frac{\langle \phi^2 \rangle}{\langle \phi \rangle^2} \sim t^{(d-4+\eta)/2}$. Hence as the temperature goes to zero, the fluctuations from mean-field theory are negligible.

### Chapter 3: RG Flowing

- The free-energy formula for RGing is a little different: $Z = \int \mathcal{D}\phi e^{-F[\phi]}$ with $F[\phi] = \int d^dx \left[ \frac{1}{2} (\nabla \phi)^2 + \frac{1}{2} \mu^2 \phi^2 + g \phi^4 + \dots \right]$. The kinetic term is pinned, the inverse temperature is absorbed into the field (this kosher because we are integrating over all field configurations in the functional integral).
- For this to coincide with our Ising model, we impose that $\mu^2 \sim T-T_c$.
- Whats the use of RG-flowing: it's a framework to calculate the critical exponents of a generic theory when mean-field approximations fails (e.g., d<4)

Three-steps to RG flow:

1. Integrate out high momentum modes ($\Lambda/\zeta < k < \Lambda$)
2. Rescale momenta ($k' = \zeta k$)
3. Rescale fields by $z$ (gradient term has coefficient equal to unity)
- In general the fields transform as $\Delta_\phi = \frac{d-2+\eta}{2}$ so that $\phi(x) \rightarrow \phi'(x') = \zeta^{\Delta_\phi}\phi(x)$
- Reduced temperature $t = |T-T_c|/T_c$
- Temperature increases upon coarse-graining: $\xi \sim t^{-\nu} \implies t\rightarrow t' = t \zeta^{1/\nu}$
- Using the fact that $F_{\text{thermo}}(t) = \int d^dx f(t)$, derive the following relations:

$f(t)\sim t^{d\nu}, \alpha = 2 - d \nu, \beta = (d-2+\eta)\nu/2, \Delta_B = d - \Delta_\phi, \gamma = \nu(2-\eta), \delta = \frac{d+2-\eta}{d-2+\eta}$

- Show that the Gaussian theory factorizes (i.e., there is no interaction between UV and IR modes)
- Show that at the Gaussian Fixed point, $\mu^2 (\zeta) = \zeta^2 \mu_0^2$, and more generally that $g_n (\zeta) = g_{n,0} \zeta^{d(1-d/2) + n}$.
- Derive Wick's theorem $\langle e^{\phi_a B_a}\rangle = e^{B_a \langle \phi_a \phi_b \rangle B_b/2}$
- Compute the renormalisation of the $\mu^2, g_0$ terms in the $\phi^4$ theory using the propagators and Wick's theoremn
- Compute the renormalisation of $\mu^2, g_0$at one and two-loops (see practice exam)

**Hint: It's quite easy once you employ Wick's theorem/Diagrammatic expansion

- Calculate the $\beta$-functions of the theory: $\beta_n = \frac{d g_n}{ds}$, where $\Lambda' = \Lambda / \zeta = \Lambda e^{-s}$
- Use the fact that $\int_{\Lambda e^{-s}}^{\Lambda} dq f(q) \sim \Lambda f(\Lambda) s$ to compute the beta functions.

## Chapter 4: Continuous Symmetry

- Phases of matter are characterized my their symmetry
- $G$ is the symmetry of the free-energy (e.g., $\mathbb{Z}_2, SO(d)$)
- $H$ is the symmetry of the ground-state configuration (e.g., $\mathbb{Z}_2, \emptyset$)
- For example, in the low-temperature state, the Ising model picks out a particular magnetization, so $H=\mathbb{Z}_2$ is spontaneously broken and the ground-state does not have a symmetry group anymore (i.e., $H=\emptyset$) below the critical temperature.
- When $B\neq0$ the Ising model no longer has a $G = \mathbb{Z}_2$ symmetry group.

Landau's approach

1. Choose an order parameter $\phi$ and a symmetry group $G$ in which it transforms under.
2. Write down the most general free-energy $f(\phi)$ subject that is invariant under $G$
3. Phases of matter are characterized by the group $H$ preserved by the ground state.
- Common model is the $O(N)$ given by $f(\phi_a) = \frac 1 2 \partial_i \phi_a \partial_i \phi_a - \frac 1 2 \mu^2 \phi_a \phi_a + g (\phi_a \phi_a)^2 + \dots$ where the field $\phi_a, a = 1,2,\dots,N$ is rotationally symmetric $\phi_a \rightarrow R_{ab}\phi_b$ with $R^T R = 1$.
- Goldstone Bosons only occur when a continuous symmetry is spontaneously broken in the ordered phase of matter (e.g., below the critical temperature, the $O(N)$ model picks out a preferred direction of $S_{N-1}$). This contrasts the Ising model in which the preferred direction is either up or down (not continuous).
- $O(N)$ picks out a mean-field value of $\langle \phi_0 \rangle = M_0 = \sqrt{-\frac{\mu^2}{4g}}$ but no preferred normal vector $n$. At a small energy cost from the gradient term, we can even vary the orientation of the field over large distances while preserving the mean $M_0$. These are pretty much soliton solutions
- There are two ways of classifying Goldstone Modes:
1. Gapless: an excitation (e.g., winding of the field) whose energy vanishes as the wavelength is brought to infinity
2. Gapped: the excitation has finite energy even when the winding has infinite wavelength. 
- Goldstones theorem: # Goldstone Bosons = $\text{dim}G - \text{dim}H$. The space of ground states (Goldstone Bosons) = $G/H$.
- An easy example of this is to look at $G = O(N)$ and $H=O(N-1)$ in the ground state (when the field picks out a particular direction). WLOG you can take $\phi_a = (M_0, 0, \dots, 0 )$ in the ground state. Then the ground-state still has an additional $O(N-1)$ symmetry on the remaining zeros. Hence the goldstrones modes take-on $O(N)/O(N-1) = S_{N-1}$
- Difference between 3d and 2d O(N) models lies in the fact that the free-energy in 2d does not depend on a particular phase angle (i.e., only derivatives of theta). In 3d the free energy  picks out a preferred angle $\theta$ due to the metric containing a $\sin^2 \theta$ term.
- Show that, for the XY model, the 2 point function obeys $\langle \theta(x) \theta(y) \rangle = \frac{1}{\gamma M_0^2} \int \frac{d^d k}{(2\pi)^d} \frac{e^{ik(x-y)}}{k^2}$
- For the X-Y model, there are not dependencies on the angle $\theta$ so the correlation function is that of massless one: $G(x-y) = \frac{1}{\gamma M_0^2}\int\frac{d^d k}{(2\pi)^d} \frac{e^{ik(x-y)}}{k^2}$.
- The critical exponents of the O(N) model are the mean field for $d\geq4$
- RG flow of the O(N) model is a little different: we have to choose which colour indices of the field we want to contract.
- Show that the renormalisation of $\mu^2$ in $O(N)$ has the form: $\mu_0^2 \rightarrow \mu_2' = \mu_0^2 + 4(N+2)g_0 \int_{\Lambda/s}^{\Lambda} \frac{d^d q}{(2\pi)^d} \frac{1}{q^2 + \mu_0^2}$. Essentially, the mass term picks up a $N+2$ contribution. If we set $N=1$ we recover the usual results previously found. For the quadratic coupling, a similar phenomena occurs: $g_{0} \rightarrow g_{0}^{\prime}=g_{0}-4(N+8) g_{0}^{2} \int_{\Lambda / \zeta}^{\Lambda} \frac{d^{d} q}{(2 \pi)^{d}} \frac{1}{\left(q^{2}+\mu_{0}^{2}\right)^{2}}$
- Why is the XY model interesting to study? Thermal fluctuations, given by the correlation function, in d=1,2. That means that there is no ordered phase in those dimensions.
- In the XY model, the lower critical dimension is 2. There is no spontaneous symmetry breaking for in d=1,2 **Mermin-Wagner Theorem.** In d=1: no gappless modes. As in QM, particle moving on SN-1 is discrete and gapped. In d=2 physics is more interesting.
- **The Mermin-Wagner theorem means that any system with a continuous symmetry has no ordered phase in d = 2 dimensions.**
- The non-linear sigma model parameterizes the O(N) field in terms of O(N-1) using a single constraint. We introduce a IR background field and UV field to perform RG on. There are some interesting results: $\frac{1}{e^{2}(\zeta)}=\zeta^{d-2}\left(\frac{1}{e_{0}^{2}}+(2-N) I_{d}\right)$
- The O(N) model has a positive Beta function for $N≥3$. In such cases, the coupling becomes very strong in the IR and weakly coupled in the UV — the theory is said to be **asymptotically free**. This is the behaviour found in QCD and Yang-Mills theory.
- The O(N) model, with unconstrained fields, has a Wilson-Fisher fixed point in dimension d = 3. This has one relevant deformation. If we turn on this relevant deformation with negative sign, we flow to the ordered phase which is described by our sigma model.
- The correlation function for the 2d XY model exhibits a log divergence: $\langle\theta(\mathbf{x}) \theta(0)\rangle=-\frac{e^{2}}{2 \pi} \log (\Lambda r)$. Using Wick's theorem, the field $\psi$ has an anomalous dimension of $\eta = \frac {e^2}{2\pi}$ ($d=2$). It is temperature dependent since the coupling $e^2 \sim t$ (i.e., it scales like the temperature). That is, the anomalous dimension increases with the coupling, and is valid at all temperatures!
- Derive the critical temperature of the Kosterlitz-Thouless transition (vortices proliferation) in 2d form first principles.
- It is also possible to RG Flow the Kosterlitz-Thouless transition.