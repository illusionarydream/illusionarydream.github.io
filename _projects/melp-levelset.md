---
layout: page
title: A Moving Least-Squares/Level-Set Particle Method for Bubble and Foam Simulation
description: A novel particle-grid scheme for simulating intricate bubble and foam flow, with MLS particles serving as interfacial trackers and surfacial discretization, enables solving both volumetric air-liquid flow and surface surfactant flow simultaneously
img: assets/img/publication_preview/melp-levelset-preview.jpg
importance: 1
category: research
related_publications: wang2024moving
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/melp-levelset/representative.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### Abstract
----

We present a novel particle-grid scheme for simulating bubble and foam flow. At the core of our approach lies a particle representation that combines the computational nature of moving least-squares particles and particle level-set methods. Specifically, we assign a dedicated particle system to each individual bubble, enabling accurate tracking of its interface evolution and topological changes in a foaming fluid system. The particles within each bubble's particle system serve dual purposes. Firstly, they function as a surface discretization, allowing for the solution of surfactant flow physics on the bubble's membrane. Additionally, these particles act as interface trackers, facilitating the evolution of the bubble's shape and topology within the multiphase fluid domain. The combination of particle systems from all bubbles contributes to the generation of an unsigned level-set field, further enhancing the simulation of coupled multiphase flow dynamics. By seamlessly integrating our particle representation into a multiphase, volumetric flow solver, our method enables the simulation of a broad range of intricate bubble and foam phenomena. These phenomena exhibit highly dynamic and complex structural evolution, as well as interfacial flow details.

<br>

<script
  defer
  src="https://cdn.jsdelivr.net/npm/img-comparison-slider@8/dist/index.js"
></script>
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/img-comparison-slider@8/dist/styles.css"
/>

<style>
    .before{
        margin: 0;
    }

    .after {
        margin: 0;
    }

    .before figcaption {
        background: #121212;
        border-radius: 0.2rem;
        color: #ffffff;
        opacity: 0.9;
        padding: 2px 10px;
        margin: 1rem;
        font-size: 1em;
        position: absolute;
        left: 0;
        bottom: 0;
        line-height: normal;
    }

    .after figcaption {
        background: #121212;
        border-radius: 0.2rem;
        color: #ffffff;
        opacity: 0.9;
        padding: 2px 10px;
        margin: 1rem;
        font-size: 1em;
        position: absolute;
        right: 0;
        bottom: 0;
        line-height: normal;
    }
</style>

### Method Overview
----

<img src="/assets/img/melp-levelset/illustration.jpg" alt="Domains" width="100%" height="auto">

<p style="text-align: center;"><b>
Illustration of domains
</b></p>

Left: The entire domain is divided into multiple volumetric regions $$\Omega_i$$ and the their interfaces $$\partial \Omega_i$$. The interfaces are treated as thin films, characterized by the local frame $$R = [{e}_1, {n}]$$ in 2D ($$R = [{e}_1, {e}_2, {n}]$$ in 3D) and thickness η, where the interfacial flow is solved.
Right: The illustration of our MLSLS particle system. Our MLSLS particle system includes two major components: a set of MLSLS particles $$\mathcal{E}$$ and a background grid $$\mathcal{G}$$. 
(1) The particles $$\mathcal{E}$$ are divided into multiple groups $$\mathcal{E}_i$$ to track the surface of each region $$\Omega_i$$. 
(2) On the background grid $$\mathcal{G}$$, we represent the implicit surface with a indicator map $$\chi_\mathcal{G}$$  and a global level set $$\phi_\mathcal{G}$$. A velocity field $$u_\mathcal{G}$$ is stored on the staggered grid. An extra set of Lagrangian particles $$\mathcal{L}$$ is introduced on the interface to track the interfacial flow across different regions.

<br>

<img src="/assets/img/melp-levelset/mpls_evo.jpg" alt="MLSLS particle evolution" width="100%" height="auto">

<p style="text-align: center;"><b>
The process of geometric evolution of our MLSLS particles system
</b></p>

(1) Advect MLSLS particles $$\mathcal{E}$$ using the velocity field $$u_\mathcal{G}$$; 
(2) Reconstruct the level-set-based implicit interfaces on the grid $$\mathcal{G}$$ using local MLS surfaces approximated on $$\mathcal{E}$$; 
(3) Correct particles $$\mathcal{E}$$ based on the grid $$\mathcal{G}$$ to achieve consistent interface representation between grid and particle and a optimal distribution; 
(4) Handle topological changes between regions including splitting and merging.

<br>


<img src="/assets/img/melp-levelset/tan_flow.jpg" alt="Interfacial flow simulation" width="100%" height="auto">

<p style="text-align: center;"><b>
The process of interfacial flow simulation
</b></p>

(1) Redistribute MLSLS particles $$\mathcal{E}$$ within each region; 
(2) Transfer physical quantities from Lagrangian particles $$\mathcal{L}$$ to MLSLS particles $$\mathcal{E}$$ in their closest two regions; 
(3) Compute interfacial geometry; 
(4) Solve tangential dynamics within each region separately; 
(5) Transfer quantities from MLSLS particles $$\mathcal{E}$$ to Lagrangian particles $$\mathcal{L}$$.

<br>

### Results
----

#### Jet on bubbles | Double bubbles

<img-comparison-slider  style="width: 49%" hover="hover">
  <figure slot="first" class="before">
    <img width="100%" src="/assets/img/melp-levelset/water_on_bubble.rendered_seq.0100.jpg">
    <figcaption>Render</figcaption>
  </figure>
  <figure slot="second" class="after">
    <img width="100%" src="/assets/img/melp-levelset/water_on_bubble_mesh_particle.mantra1.0400.jpg">
    <figcaption>Mesh</figcaption>
  </figure>
</img-comparison-slider>

<img-comparison-slider  style="width: 49%" hover="hover">
  <figure slot="first" class="before">
    <img width="100%" src="/assets/img/melp-levelset/double_bubble.render.0400.jpg">
    <figcaption>Render</figcaption>
  </figure>
  <figure slot="second" class="after">
    <img width="100%" src="/assets/img/melp-levelset/double_bubble.el.0400.jpg">
    <figcaption>Particle</figcaption>
  </figure>
</img-comparison-slider>

<br>

#### Bubble life | Multi-bubbles on water

<img-comparison-slider  style="width: 49%" hover="hover">
  <figure slot="first" class="before">
    <img width="100%" src="/assets/img/melp-levelset/bubble_life.render.0180.jpg">
    <figcaption>Render</figcaption>
  </figure>
  <figure slot="second" class="after">
    <img width="100%" src="/assets/img/melp-levelset/bubble_life.particle.0180.jpg">
    <figcaption>Particle</figcaption>
  </figure>
</img-comparison-slider>

<img-comparison-slider  style="width: 49%" hover="hover">
  <figure slot="first" class="before">
    <img width="100%" src="/assets/img/melp-levelset/in_and_out.render.0250.jpg">
    <figcaption>Render</figcaption>
  </figure>
  <figure slot="second" class="after">
    <img width="100%" src="/assets/img/melp-levelset/in_and_out.el.0250.jpg">
    <figcaption>Particle</figcaption>
  </figure>
</img-comparison-slider>

<br>

#### Four bubbles | Rising bubbles

<img-comparison-slider  style="width: 49%" hover="hover">
  <figure slot="first" class="before">
    <img width="100%" src="/assets/img/melp-levelset/four_bubbles.render.0500.jpg">
    <figcaption>Render</figcaption>
  </figure>
  <figure slot="second" class="after">
    <img width="100%" src="/assets/img/melp-levelset/four_bubbles.particle.0500.jpg">
    <figcaption>Particle</figcaption>
  </figure>
</img-comparison-slider>

<img-comparison-slider  style="width: 49%" hover="hover">
  <figure slot="first" class="before">
    <img width="100%" src="/assets/img/melp-levelset/bubble_arise.render.0120.jpg">
    <figcaption>Render</figcaption>
  </figure>
  <figure slot="second" class="after">
    <img width="100%" src="/assets/img/melp-levelset/bubble_arise.mesh.0120.jpg">
    <figcaption>Mesh</figcaption>
  </figure>
</img-comparison-slider>

<br>
<br>

### Video
----
<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/1tWclARBiHY" allowfullscreen></iframe>
</div>

<br>
<br>

### Links
----
[[DOI]](https://ieeexplore.ieee.org/document/10536666)
[[Youtube]](https://www.youtube.com/watch?v=1tWclARBiHY)

[[Preprint]](/assets/pdf/mlsls_main.pdf)
[[Preprint (Compressed)]](/assets/pdf/mlsls_compressed.pdf)
[[Preprint (Appendix)]](/assets/pdf/mlsls_app.pdf)
[[Slides for PG2024]](/assets/pdf/pg2024_mlsls.pdf)

<br>
<br>

### Bibtex

<pre>
@articl{10536666,
  author={Wang, Hui and Wang, Zhi and Hong, Shulin and Yang, Xubo and Zhu, Bo},
  journal={IEEE Transactions on Visualization and Computer Graphics}, 
  title={A Moving Least-Squares/Level-Set Particle Method for Bubble and Foam Simulation}, 
  year={2024},
  volume={},
  number={},
  pages={1-15},
  keywords={Fluids;Surfactants;Surface tension;Mathematical models;Liquids;Level set;Geometry;Level set;interface tracking;particle methods;moving least-squares;multiphase fluid;surface tension},
  doi={10.1109/TVCG.2024.3404151}
}
</pre>