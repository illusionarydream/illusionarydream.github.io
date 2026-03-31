---
layout: page
title: Codimensional Surface Tension Flow Using Moving-Least-Squares Particles
description: A novel Eulerian-Lagrangian approach to simulate various codimensional surface tension phenomena characterized by volume, thin sheets, thin filaments, and points using Moving-Least-Squares (MLS) particles
img: assets/img/publication_preview/codim-mls-preview.jpg
importance: 1
category: research
related_publications: wang2020codimensional
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/codim-mls/representative.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>
<br>

### Abstract

We propose a new Eulerian-Lagrangian approach to simulate the various surface tension phenomena characterized by volume, thin sheets, thin filaments, and points using Moving-Least-Squares (MLS) particles. At the center of our approach is a meshless Lagrangian description of the different types of codimensional geometries and their transitions using an MLS approximation. In particular, we differentiate the codimension-1 and codimension-2 geometries on Lagrangian MLS particles to precisely describe the evolution of thin sheets and filaments, and we discretize the codimension-0 operators on a background Cartesian grid for efficient volumetric processing. Physical forces including surface tension and pressure across different codimensions are coupled in a monolithic manner by solving one single linear system to evolve the surface-tension driven Navier-Stokes system in a complex non-manifold space. The codimensional transitions are handled explicitly by tracking a codimension number stored on each particle, which replaces the tedious meshing operators in a conventional mesh-based approach. Using the proposed framework, we simulate a broad array of visually appealing surface tension phenomena, including the fluid chain, bell, polygon, catenoid, and dripping, to demonstrate the efficacy of our approach in capturing the complex fluid characteristics with mixed codimensions, in a robust, versatile, and connectivity-free manner.

<br>
<br>

### Video


<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/ugJhLMlyctc" allowfullscreen></iframe>
</div>

<br>
<br>

### Links

[[DOI]](https://dl.acm.org/doi/abs/10.1145/3386569.3392487)
[[Youtube]](https://www.youtube.com/watch?v=ugJhLMlyctc)

<br>
<br>

### Bibtex

<pre>
@article{10.1145/3386569.3392487,
  author = {Wang, Hui and Jin, Yongxu and Luo, Anqi and Yang, Xubo and Zhu, Bo},
  title = {Codimensional Surface Tension Flow Using Moving-Least-Squares Particles},
  year = {2020},
  issue_date = {August 2020},
  publisher = {Association for Computing Machinery},
  address = {New York, NY, USA},
  volume = {39},
  number = {4},
  issn = {0730-0301},
  url = {https://doi.org/10.1145/3386569.3392487},
  doi = {10.1145/3386569.3392487},
  journal = {ACM Trans. Graph.},
  month = {aug},
  articleno = {42},
  numpages = {16},
  keywords = {moving-least-squares, surface tension, codimensional fluids, PIC/FLIP}
}
</pre>