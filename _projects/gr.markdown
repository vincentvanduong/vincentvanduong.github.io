---
layout: page
title: General Relativity in Mathematica
description: My General Relativity Mathematica files
img: /assets/img/gr.png
importance: 2
---

I made [three files](https://github.com/vincentvanduong/general_relativity) for my General Relativity course at McGill (PHYS 514) in Winter 2019, which was taught by Alex Maloney. They sped up a lot of the calculations, especially when dealing with index notation.


----


Here is a [Mathematica file](https://github.com/vincentvanduong/general_relativity/blob/main/metricTransformation.nb) that will do all the index summation necessary for doing basic physics in **flat spacetime such** as:

* Computing the Jacobian of a coordinate transformation: $$ \frac{\partial x^{\mu'}}{\partial x^\nu} $$

* Representing the Minkowski metric in a new coordinate system: $$ \eta_{\mu' \nu'} $$

* Calculating the new line element: $$ ds'^2 $$

* Determining the Christoffel symbols: $$ \Gamma_{\mu \nu}^{\lambda} $$

----

Here is a [Mathematica file](https://github.com/vincentvanduong/general_relativity/blob/main/problem1prime.nb) that will do all the index summation necessary for doing physics in an **arbitrary background (spacetime)** such as calculating the:

* Christoffel symbols: $$ \Gamma_{\mu \nu}^{\lambda} $$

* Riemann Tensor: $$ R_{\mu \rho \nu \sigma} $$

* Ricci Tensor: $$ R_{\mu \nu} $$

* Ricci Scalar: $$ R $$

* Einstein Tensor: $$ G_{\mu \nu} $$

* Stress Tensor: $$ T_{\mu \nu} $$

----

Finally, here is a [Mathematica file](https://github.com/vincentvanduong/general_relativity/blob/main/Problem%2B3.nb) that verifies the solution of the **Kerr metric**.