---
layout: page
title: My Statistical Field Theory Notes
description: Repertoire of important formulae useful for phase transitions
img: /assets/img/mexicanhat.png
importance: 3
---

# Purpose

This course *fluctuates* highly in difficulty, so I am building these notes to help me understand the harder parts. How do I calculate critical exponents of a theory? How can I draw a phase diagram from first principles? How do I renormalize a field and compute its beta functions? How does Wick's theorem help me compute the RG flow equations? What the hell are even Goldstone Bosons? These notes will answer some of these questions!

My page will highlight David Tong's Statistical Field Theory notes given at Cambridge. 

# Section I: From Spins to Fields

## Ising Model (mean field approximation)

The Ising model is perhaps the simplest system we can study, yet it is rich in physics.  Let $$ m $$ be the **mean field** of the lattice. Then we can write the partition function as

$$ e^{-\beta F_{\text{thermo}}} = Z = \sum_{\{s_i\}} e^{-\beta E[s_i]} = \sum_m \sum_{\{s_i\}|_m} e^{-\beta E[s_i]} $$

Thus, we have split the sum over all spins into two:
1. Sum over all average magnetizations
2. Sum over all spin configurations given a fixed average magnetization.

These are clearly equivalent by a similar idea to the law of total probability. We can now write the second term in the sum as a function of $$ m $$ only:

$$ \sum_{\{s_i\}|_m} e^{-\beta E[s_i]} = e^{- \beta N f(m)} $$

Here, $$ f(m) $$ can be interpreted as the free-energy per lattice site. This is our first instance of **coarse-graining**. The sum over average magnetizations can be approximated as an integral:

$$ \sum_{\{s_i\}} \sim \int_{-1}^{+1}dm $$ 

which helps us write our partition function as:

$$ e^{-\beta F_{\text{thermo}}} = Z \sim \int_{-1}^{+1}dm e^{- \beta N f(m)} $$

But all these steps come at a cost: we do not know how to compute e^{- \beta N f(m)} because computing the restricted sum is difficult. We can get around this using the **saddle-point approximation**, in which we only keep the most degenerate value multiplied by the degeneracy $$ \Omega $$. In particuar,

$$ e^{- \beta N f(m)} = \sum_{\{s_i\}|_m} e^{-\beta E[s_i]} \sim \Omega(m)e^{-\beta N E[m]} $$

For a system with $$ N $$ spins, we can calculate the multiplicity via
$$ \Omega = \frac{N!}{N_{\up}! N_{\down}!} = \frac{N!}{N_{\up}!(N-N_{\up})!} $$

$$ m = \frac{N_{\up}-N_{\down}}{N} = \frac{2N_{\up}-N}{N} $$

So that 

$$ f(m) = E[m] - T \frac{1}{N} \log{\Omega} $$

Using Stirling's approximation: $$ \log \Omega = N\left(\log 2 + \tfrac{1}{2}(1+m)\log{(1-m)} + \frac{1}{2}(1-m)\log(1-m) \right) $$. We now plug-in the energy of the system at each lattice site $$ E[m] = -Bm - \frac{1}{2}Jqm^2 $$.

Hence,

$$ f(m) = -B m-\frac{1}{2} J q m^{2}-T\left(\log 2-\frac{1}{2}(1+m) \log (1+m)-\frac{1}{2}(1-m) \log (1-m)\right) $$

The function $$ f(m) $$ takes on the minimum value if we are to reach a thermodynamic equilibrium. Hence

$$ \frac{\partial f}{\partial m} = 0 \implies m = \tanh{\beta(Jqm + B)} $$

which is a self-consistency equation for the mean-field approximation. 

Alternatively, we could also Taylor expand in Mathematica, we get 

$$ f(m) = - T \log2  - Bm + \frac{1}{2}(T-Jq)m^2 + \frac{1}{12}Tm^4 + \frac{1}{30}Tm^6 + \mathcal{O}(m^8) $$

We get two solutions for the field magnetization:

$$ m = \pm \sqrt{\frac{3(T - Jq)}{T}} $$

We still have some unanswered questions:

1. What does the phase diagram look like?
2. What are the citical exponents ($$ \alpha, \gamma, \delta, \nu, \xi $$) of the theory?

and **how do we calculate them?**

## Functional Derivatives, Source Fields, Correlation Functions, Legendre Transformations, and Green's Functions

This is my favourite conceptual piece of the course because it ties in some rich mathematics into something that is physical.

Let's start with the free-energy of a field configuration. It is a functional:

$$ F[\phi] = \int d^d x \frac{1}{2}\left[(\nabla\phi)^2 + \mu^2 \phi^2 \right] = \int \frac{d^d k}{(2\pi)^d}\frac{1}{2}\left[ k^2 + \mu^2\right]\phi_k \phi_{-k} $$

And it can be modified by adding a spatially varying external field $$ J(x) $$. You can think of this as an external magnetic field coupling to the spins on the lattice. To this end, the new free-energy is

$$ F[\phi,J] = \int d^d x \left[\frac{1}{2}(\nabla\phi)^2 + \frac{1}{2}\mu^2 \phi^2 - J(x)\phi(x)\right]  = \int \frac{d^d k}{(2\pi)^d}\left[ \frac{1}{2}k^2 + \frac{1}{2}\mu^2\right]\phi_k \phi_{-k} - \phi_k J_{-k}$$

We can symmetrize the term with the source field to obtain

$$ F[\phi,J] = \int \frac{d^d k}{(2\pi)^d}\frac{1}{2}\left[ (k^2 + \mu^2)\phi_k \phi_{-k} - \phi_k J_{-k} - \phi_{-k}J_k \right]$$

The terms under the integral sign are quadratic in the field $$ \phi $$ but not a perfect square. We can try to define a new a field that will complete the square:

$$ \tilde{\phi}_k = \phi_k + a_k J_k $$

for some unknown function $$ a_k $$. Indeed, we can turn the crank to show that if we choose

$$ a_k = - \frac{1}{k^2 + \mu^2} $$

i.e., 1/quadratic part of the energy, then

$$ (k^2 + \mu^2)\phi_k \phi_{-k} - \phi_k J_{-k} - \phi_{-k}J_k = (k^2 + \mu^2)\tilde{\phi}_k\tilde{\phi}_{-k} - \frac{J_k J_{-k}}{k^2 + \mu^2} $$

which "completes the square". How can we interpret the new field? It is a field shifted by a term proportional to the external sources and surpressed by its total energy. In particular, the shifted field is unaffected by high momentum modes or if it has a large mass. When computing the statistics using this new field, we pick up a term which grows as

$$ - \frac{J_k J_{-k}}{k^2 + \mu^2} $$

Upon analytic continuation, if we can get $$ k^2 = -m^2 $$ , then we hit a resonance and the theory blows up unless $$ J(k) $$ is suitably well-behaved to cancel such poles.

We can calculte the partition function of original theory by setting $$ J = 0 $$ at the very end. So let's now write the partition function in the presense of an external source $$ J(x) $$ by:

$$ Z[J(x)] = \int \mathcal{D}\phi e^{-\beta F[\phi]}e^{\beta \int d^dx' J(x')\phi(x')} $$

Taking **functional derivatives** gives us the moments of the theory. As a warm-up, we define:

$$ \frac{\delta}{\delta J(x)} \int d^dx' f(x')J(x') = \int d^dx' f(x') \frac{\delta J(x')}{\delta J(x)} = \int f(x') \delta^{(d)}(x-x') = f(x) $$

so that

$$ \frac{\delta}{\delta J(x)} Z = \beta \int \mathcal{D} \phi \phi(x) e^{-\beta F[\phi]}e^{\beta \int d^dx' J(x')\phi(x')} $$

and 

$$ \left\langle \phi(x) \right\rangle_J = \frac{1}{\beta}\frac{\delta}{\delta J(x)} \log Z[J] $$

We can combine both results to compute some really func quantities.  First let's compute the partition function $$ Z[J] $$ in the presense of an external source field:

$$ Z[J] = \int \mathcal{D}\phi_k \mathc \exp{-}