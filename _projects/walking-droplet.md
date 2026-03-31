---
layout: page
title: A Two-Way Coupling Approach for Simulating Bouncing Droplets
description: A two-way coupling cut-cell approach to simulate bouncing droplet phenomena by incorporating the lubricated thin aerodynamic gap between fluid volumes
img: assets/img/publication_preview/walking-droplet-preview.jpg
importance: 1
category: research
related_publications: wang2024walking
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/walking-droplet/representative.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<br>

### Abstract
----

This paper presents a two-way coupling approach to simulate bouncing droplet phenomena by incorporating the lubricated thin aerodynamic gap between fluid volumes. At the heart of our framework lies a cut-cell representation of the thin air film between colliding liquid fluid volumes. The air pressures within the thin film, modeled using a reduced fluid model based on the lubrication theory, are coupled with the volumetric liquid pressures by the gradient across the liquid-air interfaces and solved in a monolithic two-way coupling system. Our method can accurately solve liquid-liquid interaction with air films without adaptive grid refinements, enabling accurate simulation of many novel surface-tension-driven phenomena such as droplet collisions, bouncing droplets, and promenading pairs.

<br>

### Video
----

<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/WxcVmrmByVU?si=fm79BnCM6AcivJTh" allowfullscreen></iframe>
</div>

<br>

### Overview
----

<style>
    .grid-container {
        display: grid;
        grid-template-columns: repeat(6, 1fr);
        /* grid-gap: 10px;  */
    }

    .grid-item {
        /* background-color: #ccc; */
        /* text-align: center;
        font-size: 20px;
        padding: 20px; */
    }
    .item1 { grid-column: span 2; grid-row: span 2; }
    .item2 { grid-column: span 2; grid-row: span 2; }
    .item3 { grid-column: span 2; grid-row: span 1; }
    .item4 { grid-column: span 2; grid-row: span 1; }
    /* .item5 { grid-column: span 2; grid-row: span 1; } */
</style>

<img src="/assets/img/walking-droplet/domains.jpg" alt="Domains" width="100%" height="auto">

<p style="text-align: center;"><b>
Illustration of fluid domains and interfaces
</b></p>

The entire computational domain is divided into three domains. $$\Omega_1$$ is liquid, $$\Omega_2$$ is the thin air film, and $$\Omega_3$$ is ambient air. We show examples of the domain evolution at $$t = \{0, t_1, t_2\}$$. 

<br>

<img src="/assets/img/walking-droplet/grid.jpg" alt="Grids" width="100%" height="auto">

<p style="text-align: center;"><b>
Discretization of liquids and the air film
</b></p>

The liquid domain $$\Omega_1$$ (blue) is divided into several separate
liquid volumes on the Cartesian grid enhanced by cut-cells, with level set $$\phi$$, pressure $$p_1$$ and velocity $$u$$ sampled on
nodes, cells, and faces. In the gap between liquid volumes, the air film $$\Omega_2$$ (green) is represented by single-layered
irregular cells and the cut-cell meshes to solve pressure $$p_2$$.

<br>

<img src="/assets/img/walking-droplet/liquid_grid.jpg" alt="Grids" width="100%" height="auto">

<p style="text-align: center;"><b>
Discretization of the liquid level set, velocity, and pressure
</b></p>

We split the liquid domain into multiple liquid regions $$(\Omega_{1,1}, \Omega_{1,2}, ...)$$. Left and Right: Each region has its own node-based level set $$\phi$$ (black dots) and face-based velocity field $$u$$ (solid arrows). The interfaces $$\partial\Omega_1$$ are discretized into the cut-cell mesh (blue segments) by performing the marching cubes algorithm on level sets. The velocity fields are sampled on grid faces (solid arrows) and extrapolated (dashed arrows). Middle: When coupling fluid regions with the air film (green), the normal velocities on the cut faces (dashed arrows) are interpolated from the grid faces. The pressure samples (blue dots) in the cut-cell are repositioned on the same iso-distance (blue dotted lines) parallel to the interface, following [70].

<br>

### Results
----

<img src="/assets/img/walking-droplet/binary_all.jpg" alt="" width="100%" height="auto">

<p style="text-align: center;"><b>
Binary droplet collision
</b></p>

Top and Bottom: Representative frames of the rendered images from our simulation and the experimental snapshots from [1]. Middle: The evolution of the $$x$$-axis positions of two droplets. The regions filled by the light color are the $$x$$-axis bounding box of two droplets. Solid lines denote the $$x$$-axis center position of two droplets.

<br>

<img src="/assets/img/walking-droplet/bounce_trajectory.jpg" alt="" width="100%" height="auto">

<p style="text-align: center;"><b>
A droplet bouncing on a vibrating bath in (2,1) mode
</b></p>

Top: Rendered images of four representative frames. Bottom: Temporal evolution of the scene. The solid line denotes the movement of the droplet center, and the dashed line denotes the bath movement. 

<br>

<div class="grid-container">
    <div class="grid-item item1">
        <img src="/assets/img/walking-droplet/promenade_closer.png" alt="Promenading pair" width="100%" height="auto">
    </div>
    <div class="grid-item item2">
        <img src="/assets/img/walking-droplet/promenade_further.png" alt="Promenading pair" width="100%" height="auto">
    </div>
    <div class="grid-item item3">
        <img src="/assets/img/walking-droplet/promenading_dist.jpg" alt="Promenading pair dist" width="100%" height="auto">
    </div>
    <div class="grid-item item4">
        <img src="/assets/img/walking-droplet/promenading_pos.jpg" alt="Promenading pair pos" width="100%" height="auto">
    </div>
</div>

<p style="text-align: center;"><b>
Promenading pairs
</b></p>

The two droplets bounce on the vibrating bath and form the promenading pairs. 
Left: Rendered result for Case I, where two droplets bounce and move away from each other. 
Middle: Rendered result for Case II, where the  droplets move towards each other. 
Right top: The droplet positions as a function of time $$t$$. The colored stripes indicate the $$x$$-axis bounding box of droplets. The solid lines represent the trajectories of the droplet centers. 
Right bottom: The droplet distances as a function of time $$t$$.

<br>

<img src="/assets/img/walking-droplet/merge_droplet.png" alt="" width="100%" height="auto">

<p style="text-align: center;"><b>
Droplet merging and pinching
</b></p>

A large droplet falls and merges with the bath, which causes a thin liquid column to form due to the surface tension. The column eventually breaks off and pinches off a smaller droplet bouncing on the bath.

<br>

### Links
----

<!-- [[Preprint on SSRN]](http://ssrn.com/abstract=4579924) -->
<!-- [[Preprint]](/assets/pdf/walking_droplet_ijnme_pre.pdf)
[[Preprint (Compressed)]](/assets/pdf/walking_droplet_ijnme_pre_compressed.pdf) -->
[[URL]](https://onlinelibrary.wiley.com/doi/abs/10.1002/nme.7592)
[[Youtube]](https://www.youtube.com/watch?v=WxcVmrmByVU)

<br>

<!-- ### Citation

<pre>
Wang, Hui and Xiao, Yuwei and Mao, Yankai and Xiong, Shiying and Yang, Xubo and Zhu, Bo, A Two-Way Coupling Approach for Simulating Bouncing Droplets. 
Available at SSRN: https://ssrn.com/abstract=4579924 or http://dx.doi.org/10.2139/ssrn.4579924
</pre> -->