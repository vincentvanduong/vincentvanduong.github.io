---
layout: page
title: Correlation functions, two-point functions, Greens functions, and propogators -- what's it all about?
description: I discuss the relationsship between these quantities and what they're good for in physics. 
img: /assets/img/1.jpg
importance: 3
---

### Purpose

Within quantum field theory and statistical physics, these functions are readily used. However, these functions are usually introduced through different contexts and approaches. I'll try to maket he picture clearer, starting more-or-less from scratch.

### So what?

These functions are building blocks for physics theories. When you obtain good grasp of a "two-point" function then you have a good intuition for the underlying physics involved. On the theoretical side, "propogators" allow quick Feynman diagram calcualtions. For experiementalists, correlation functions are truly observables.

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
