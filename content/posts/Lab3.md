---
title: "Master 2 - Human Computer Interaction: Reconstructing Myself in 3D with Gaussian Splatting (Unity)"
date: 2025-10-31
description: "A hybrid scientific and practical exploration of Gaussian Splatting, including theory, pipeline, and a personal 3D reconstruction imported into Unity."
tags: ["Gaussian Splatting", "Unity", "3D Reconstruction", "Computer Vision", "Master VAR", "Human-Centered Computing"]
---

*A hybrid exploration of the science behind Gaussian Splatting and my own 3D reconstruction pipeline.*  
*Master’s in Computer Vision & AI — Gustavo*

This blog post combines both the **theoretical concepts** from the lecture slides and the **practical experiment** where I reconstructed **myself** and rendered the final Gaussian model in Unity.

---
<!--more-->


Gaussian Splatting is one of the most visually striking and technically powerful modern approaches to **3D reconstruction** from images. Unlike classical volumetric methods such as NeRFs, Gaussian Splatting represents a scene as a cloud of **anisotropic 3D Gaussians**, each with learned parameters such as position, scale, rotation, opacity, and spherical harmonic color coefficients.  


# 1. Understanding Gaussian Splatting

Gaussian Splatting works by optimizing a set of 3D Gaussians whose parameters are adjusted to match captured 2D images through differentiable rasterization.  
Key components include:

- **Gaussian primitives:** Each Gaussian stores geometry + appearance information.  
- **Spherical Harmonics (SH):** Used for view-dependent color.  
- **Densification:** Gaussians split or merge as needed to improve detail.  
- **Differentiable splatting:** Each Gaussian is projected into screen space as an ellipse.  

This method avoids the slow raymarching used in NeRFs and achieves **real-time rendering**, making it ideal for interactive applications such as Unity.


# 2. My Pipeline: From Real Life to a Unity 3D Reconstruction

To better understand the pipeline, I decided to reconstruct **myself** using Gaussian Splatting and render the result inside Unity.

The process involved four major stages:

## 2.1 Image Capture
I captured a set of images of myself while rotating in place under stable lighting. These images provided the multi-view input required for reconstructing geometry and color.

## 2.2 Gaussian Splatting Optimization
The optimization phase estimated:

- 3D positions  
- scales and rotations  
- opacity  
- spherical harmonic colors  
- visibility weights  

## 2.3 Exporting Model Files

The training generated several core files:

- `_col` — color SH coefficients  
- `_shs` — spherical harmonics  
- `_pos` — Gaussian positions  
- `_oth` — additional data  
- `_chk` — checkpoint  

These files collectively describe the 3D Gaussian scene. However, the main one is the .ply file, which contains all the gaussian and effectively the 3D scene.

## 2.4 Importing into Unity (URP)

Unity’s Gaussian Splatting loader can import the .ply inside a folder such as:

```
Assets/GaussianAssets/Gustavo/
```

The model then appears instantly in the Unity Scene, rendered in real-time.



# 3. The Result in Unity
After importing into unity, here is the result:

![Gaussian Splatting Unity](/assets/gaussian_splatting_unity.png)

(as you can see, it's me jamming some music)


# 4. Observations From My Experiment

### ✔ Lighting and Color Fidelity  
The reconstructed model retains strong color consistency thanks to spherical harmonics.

### ✔ Real-Time Rendering  
The model renders smoothly inside Unity even with thousands of Gaussian primitives.

### ✔ Imperfections  
Thin structures such as fingers or glasses may appear noisy when not captured with enough viewpoints.

### ✔ Ideal for VR/AR  
The method supports responsive, interactive 6DoF viewing with minimal overhead.


# 5. Conclusion

This experiment helped me understand the full lifecycle of Gaussian Splatting:

- It merges computer vision, graphics, and optimization.
- Provides impressive real-time rendering performance.
- Produces highly realistic 3D reconstructions from simple image captures.
- Integrates smoothly with real-time engines like Unity.

Overall, Gaussian Splatting allowed me to create a **3D avatar of myself**, going from real images → optimized Gaussians → interactive rendering.  
It is both a powerful research tool and a practical method for future XR and visualization applications.

