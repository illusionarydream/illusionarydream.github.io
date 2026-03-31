---
layout: page
title: A CNN-based Flow Correction Method for Fast Preview
description: A CNN-based method to correct the overall shape of a low-resolution simulation to closely follow the shape of the high-resolution version
img: assets/img/publication_preview/flow-correct-preview.jpg
importance: 1
category: research
related_publications: xiao2019cnn
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/flow-correct/representative.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Shape correction examples for three-dimensional case. Our ML-based method corrects the overall shape of a low-resolution simulation to closely follow the shape of the high-resolution version.
</div>

<br>

### Abstract

Eulerian-based smoke simulations are sensitive to the initial parameters and grid resolutions. Due to the numerical dissipation on different levels of the grid and the nonlinearity of the governing equations, the differences in simulation resolutions will result in different results. This makes it challenging for artists to preview the animation results based on low-resolution simulations. In this paper, we propose a learning-based flow correction method for fast previewing based on low-resolution smoke simulations. The main components of our approach lie in a deep convolutional neural network, a grid-layer feature vector and a special loss function. We provide a novel matching model to represent the relationship between low-resolution and high-resolution smoke simulations and correct the overall shape of a low-resolution simulation to closely follow the shape of a high-resolution down-sampled version. We introduce the grid-layer concept to effectively represent the 3D fluid shape, which can also reduce the input and output dimensions. We design a special loss function for the fluid divergence-free constraint in the neural network training process. We have demonstrated the efficacy and the generality of our approach by simulating a diversity of animations deviating from the original training set. In addition, we have integrated our approach into an existing fluid simulation framework to showcase its wide applications.

<!-- ### Video

<iframe width="560" height="315"
src="https://www.youtube.com/embed/ugJhLMlyctc" 
frameborder="0" 
allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
allowfullscreen>
</iframe> -->

<br>

### Links

[[DOI]](https://doi.org/10.1111/cgf.13649)

<br>

### Bibtex

<pre>
@article{10.1111:cgf.13649,
author = {Xiao, Xiangyun and Wang, Hui and Yang, Xubo},
title = {A CNN-based Flow Correction Method for Fast Preview},
journal = {Computer Graphics Forum},
volume = {38},
number = {2},
pages = {431-440},
doi = {https://doi.org/10.1111/cgf.13649},
url = {https://onlinelibrary.wiley.com/doi/abs/10.1111/cgf.13649},
eprint = {https://onlinelibrary.wiley.com/doi/pdf/10.1111/cgf.13649},
abstract = {Abstract Eulerian-based smoke simulations are sensitive to the initial parameters and grid resolutions. Due to the numerical dissipation on different levels of the grid and the nonlinearity of the governing equations, the differences in simulation resolutions will result in different results. This makes it challenging for artists to preview the animation results based on low-resolution simulations. In this paper, we propose a learning-based flow correction method for fast previewing based on low-resolution smoke simulations. The main components of our approach lie in a deep convolutional neural network, a grid-layer feature vector and a special loss function. We provide a novel matching model to represent the relationship between low-resolution and high-resolution smoke simulations and correct the overall shape of a low-resolution simulation to closely follow the shape of a high-resolution down-sampled version. We introduce the grid-layer concept to effectively represent the 3D fluid shape, which can also reduce the input and output dimensions. We design a special loss function for the fluid divergence-free constraint in the neural network training process. We have demonstrated the efficacy and the generality of our approach by simulating a diversity of animations deviating from the original training set. In addition, we have integrated our approach into an existing fluid simulation framework to showcase its wide applications.},
year = {2019}
}
</pre>