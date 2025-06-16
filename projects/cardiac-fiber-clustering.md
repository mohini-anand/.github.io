---
layout: project
title: "Deep Learning for Cardiac Fiber Architecture Analysis"
description: "Unsupervised clustering of myocardial fibers from DTI data using sequential and global representations"
date: 2024-01-15
image: /assets/images/cardiac-dti/cardiac-overview.png
tags: [deep-learning, medical-imaging, cardiac-dti, unsupervised-learning]
---

# Unraveling the Heart's Underlying Architecture

<div class="project-hero">
  <img src="../images/project-images/fiber-clustering/flow diagram.png" alt="Example of clustered cardiac fibers">
  <p class="caption">Example of clustered cardiac fibers enabling deeper understanding of the heart's architecture</p>
</div>

### Key Innovations

1. I calculated the following **Anatomically-Informed Features**
   - Helical Angle (HA): Captures transmural fiber rotation
   - Transmural Depth (TD): Normalizes position within heart wall
   - Enables separation of spatially overlapping but functionally distinct fibers

2. **Dual Representation Learning**
   - **BLSTM Network**: Learns local sequential dependencies by predicting future fiber points
   - **Transformer Autoencoder**: Captures global trajectory shapes through self-attention
   - Fusion creates comprehensive fiber representations

3. **Robust Clustering**
   - HDBSCAN automatically determines cluster numbers
   - Handles variable fiber densities
   - Identifies outliers that may indicate diseased regions


