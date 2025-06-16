# Unraveling the Heart's Underlying Architecture

## The Challenge

The heart's muscle fibers form an intricate 3D architecture that's critical for pumping function. When disease disrupts this architecture, it can lead to heart failure. Often, pathologies result in permanent damage to the myocardial architecture resulting in chronic dysfunction and weakness in the heart's mechnical abilities. Thus, it is crucial to quantify these structural changes even after they have occured to be able to understand WHY and HOW these changes affect the overall mechanical function of the heart.

 Yet analyzing these complex, intertwining fiber patterns from Diffusion Tensor Imaging (DTI) data remains one of cardiology's significant unsolved challenges. Current methods focus on localized regions and average metrics, missing the global patterns that define cardiac function. The heart lacks the distinct anatomical landmarks found in brain imaging, and cardiac fibers extensively overlap without clear endpoints, making traditional analysis methods ineffective.

## My Approach

I developed a novel deep learning framework that learns to understand cardiac fiber architecture by combining local sequential patterns with global shape understanding. My key insight was that cardiac fibers, while spatially overlapping, have distinct functional properties that can be captured through careful feature engineering and dual representation learning.


<div class="methodology-figure">
  <img src="../images/project-images/fiber-clustering/flow diagram.png" alt="Framework overview">
  <p class="caption">My dual-representation approach: BLSTM captures local progression while Transformer learns global patterns</p>
</div>

I first extract anatomically meaningful features for each fiber point: the Helical Angle (HA) that captures transmural fiber rotation, and Transmural Depth (TD) that normalizes position within the heart wall. These features, combined with spatial coordinates, provide rich information about each fiber's trajectory and anatomical context.

For representation learning, I employ a dual approach. I train a Bidirectional LSTM network with a novel pretext task—predicting the next 25 points along a fiber trajectory. This forces the network to learn local sequential dependencies and understand how fibers progress through the myocardium. Simultaneously, I use a Transformer-based autoencoder to capture global trajectory shapes through self-attention mechanisms across all points in a fiber. By fusing these complementary representations, I create comprehensive embeddings that capture both local and global fiber characteristics.

Finally, I apply HDBSCAN clustering to these learned representations. This density-based approach automatically determines the number of clusters, handles the heart's variable fiber densities, and identifies outliers that may indicate diseased regions. The result is an unprecedented delineation of cardiac fiber architecture, revealing 33-62 anatomically meaningful fiber populations that previous methods would merge together.

## Technical Depth

This project represents a unique intersection of multiple technical domains. The computer graphics aspects involve analyzing results on complex 3D meshes of cardiac fibers and extracting appropriate boundaries for transmural depth calculation. I implemented mathematical modeling through Laplace-Dirichlet boundary value problems solved with finite element methods to compute normalized transmural distances. The deep learning component encompasses both sequential modeling with LSTMs and global pattern recognition with Transformers, requiring careful architecture design and training strategies. Perhaps most challenging is the visualization aspect—converting clustered fiber trajectories into meaningful 3D surfaces for clinical interpretation proves surprisingly non-trivial and remains an active area of my research.

## Current Progress and Vision

While my clustering pipeline is complete and validated on canine cardiac DTI data, I'm currently replicating this method on a porcine heart DTI dataset to demonstrate cross-species generalizability. The next major milestone involves developing sophisticated visualization techniques that can convert fiber clusters into interpretable 3D surfaces, making the results accessible to clinicians who aren't familiar with tractography representations.

My long-term vision is to create a tool that cardiac surgeons and cardiologists can use in clinical settings. By understanding patient-specific fiber architecture before procedures, clinicians could better predict outcomes and tailor interventions. This could be particularly valuable for planning ablation procedures, assessing infarct boundaries, or monitoring how therapies affect cardiac structure over time.

