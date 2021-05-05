---
layout: page
title: My Quantum Field Theory Tricks and Tips
description: I introduce useful prescriptions for QFT calculations (e.g., currents, stress-tensors, hamiltonians, canonical momenta) 
img: /assets/img/springmattress.jpeg
importance: 3
---

### Purpose

I usually run into similar QFT calculations over and over again. I'll present some short-cuts/algorithms for computing them -- I hope they can also help you 😎


### Conserved current $$ j^{\mu} $$

How does the Lagrangian change under a *continuous* transformation? For example, a spacial translation of the system $$ x\mapsto x+a $$ or a field redefinition $$ \phi^a \mapsto M^{a}_b \phi^b $$ or even a mix of both.  **Noether's theorem** tells us that for any continuous symmetry of the Lagrangian which leaves the action invariant, there is an associated conserved current $$ j^\mu $$ (i.e., $$ \partial_\mu j^\mu = 0 $$). 

Here comes the prescription:

1. Identify the transformation at the infinitessimal scale
2. Calculate the associated field transformation: $$ \delta \phi $$
3. Calculate the associated Langrangian transformation: $$ \delta \mathcal{L} = \partial_\mu \mathcal{J}^\mu $$
4. Equate the two:
$$ j^\mu = \frac{\partial \mathcal{L}}{\partial(\partial_\mu \phi)} \delta \phi - \mathcal{J}^\mu $$
5. Strip out the components of the current if it is in index-free notation.

The main idea in this equation is to associate divergences to boundary terms (this should make you think of Gauss's law or any Green identity)

#### Example 1: Vector field theory $$ \phi_a $$ with $$ SO(3) $$ rotations

1. The associated transformation is: $$ \phi_a \mapsto R(\theta\hat{\eta})^{b}_a \phi_b $$
2. Expanding at small angles yields
$$ R(\theta \hat{\eta})^b_a \phi_b = \phi_a + \theta \epsilon_{abc} \eta_b \phi_c $$.
We identify
$$ \delta \phi_a = \theta \epsilon_{abc} \eta_b \phi_c $$.
3. We see that $$\delta \mathcal{L} = 0 $$ because under such a transformation the Lagrangian is completely unchanged. So $$ 
\mathcal{J}^\mu = 0 $$ since no boundary terms appear! This is obvious because the transformation is associated to **fields** and not coordinates.
4. We now construct the associated conserved current
$$ j^\mu = \frac{\partial \mathcal{L}}{\partial(\partial_\mu \phi)} \delta \phi - \mathcal{J}^\mu $$ which amounts to
$$ j^\mu = (\theta \epsilon_{abc}\eta_b \phi_c)(\partial^\mu \phi_a) = \theta(\epsilon_{abc}\partial^\mu \phi_a \phi_c)$$
5. We can strip out components associated with the unit vector $$ \hat{\eta} $$:
$$j^\mu_a = \epsilon_{abc} \partial^\mu \phi_b \phi_c $$

What is the physical interpretation of this conserved current? Let's look at the $$ \mu = 0, a=1 $$ component:

$$j^0_1 = \epsilon_{1bc}\dot{\phi_b}\phi_c = \dot{\phi_2}\phi_3 - \dot{\phi_3}\phi_2 $$.

This reminds us of the field's angular momement in the $$a=1$$ direction. How do spatial components of this current look like?

$$j^i_1 = -(\partial_1 \phi_2) \phi_3 + (\partial_1 \phi_3) \phi_2 $$

This reminds us of a curl/torsion.  We can thus interpret the conserved current as following: **the angular momentum coming into the field results in a net spatial torsion.**

#### Example 2: Scalar field theory $$ \phi $$ with conformal symmetry (TO-DO).



1. The associated transformations are: $$x \mapsto \lambda x, \phi(x) \mapsto \phi'(x) = \lambda^{-D}\phi(\lambda^{-1}x) $$. 
2. Expanding at small scaling ($$ \lambda = 1+\epsilon $$ ): $$\delta phi = -\epsilon(D + x^\nu \partial_\nu)\phi
3. Since the action is invariant, the Lagrangian is invariant up to a total derivative: $$ \delta \mathcal{L} = -\epsilon x^\nu \partial_\nu \mathcal{L} = -epsilon x^\nu() $$
4. Constructing the associated current
### Warm-up

I'll assume you have a basic understanding of the statistical mechanics to start our discussion. So let's talk about the 1D Ising model on a circle (i.e. periodic boundary conditions.) Let's use $$ N $$ spins with an external magnetic $$ J_i $$ that depends on the lattice point $$ i $$. Then the energy of a specific configuration of spins is:

$$ E[\{S_i\}_{i=1}^N] = -\sum_{i=1}^{N}\left(S_i S_{i+1} + J_i S_i\right) $$

I normalized coefficients for convenience, but they can be restored later-on. Let's remember that the energy is a function of the spin configuration $$ \{S_i\}_{i=1}^N $$ -- this is a discrete analog of a functional which we will see later. For example, energy functionals will take-in a spin configuration that varies continuously in space. For our spins on the circle, a few configurations with three spins involved can look like

$$ ( \uparrow, \downarrow, \downarrow ), ( \uparrow, \uparrow, \uparrow ), ( \downarrow, \downarrow, \downarrow ), \cdots $$





Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

To give your project a background in the portfolio page, just add the img tag to the front matter like so:

    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/1.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/3.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/5.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/5.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal it's glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/6.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/11.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/" target="_blank">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/6.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/11.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
```
