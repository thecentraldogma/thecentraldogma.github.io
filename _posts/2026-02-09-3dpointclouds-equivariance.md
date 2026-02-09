---
layout: post
title: "3D point cloud problems often require equivariance"
date: 2026-02-09
mathjax: true
---

It turns out that modeling molecules in 3D is not the only application that requires baking in the notion of rotational- and translational- equivariance into neural networks. I recently learnt that modeling 3D objects using 3D point clouds also involves similar constraints. 

For example, the use of AI in the dental industry is rapidly growing. In particular, dental labs currently spend long manual hours digitally designing the 3D shape of dental prosthetics like crowns in a CAD-like software. This process is obviously highly personalized since the designed crown has to respect the exact geometry of adjacent and opposing teeth of an individual. The starting point therefore is often a 3D point cloud of the patients teeth created using an intraoral scanner (which itself is a relatively recent step up from bite impressions in a clay-like material). 

However, the manual design process can be replaced by a generative AI model if the model can create the 3D point cloud of the desired crown with good enough fidelity. Now, in writing a DDPM model for generating the 3D cloud for a prosthetic crown, we do not really care how exactly the 3D point cloud of the patients intra-oral scan is oriented or translated relative to the 3D origin: regradless of rotation or translation, the point cloud represents the same intra-oral geometry. This means that whatever model architecture we chose to write as a de-noiser, it must not only be permutation equivariant (swapping points makes no difference to 3D geometry, unlike swapping pixels in an image fed to a CNN), but also rotational equivariance and translation invariance. That is, if we rotate the input 3D cloud of the patients teeth arbitrarily, the predict noise in 3 dimensions must rotate the same way, and if we translate the patients 3d point cloud, it should have no effect on the predicted noise. Naturally, the many arhcitectures that have been proposed in the last 5 years for preserving such symmetries are very useful -- SE3-Transformers, Tensor Field networks, which both use sphericla harmonics, and the simpler Equivariance Graph Neural Networks. 
