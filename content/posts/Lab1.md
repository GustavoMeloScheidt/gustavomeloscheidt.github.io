---
title: "Master 2 - Human Computer Interaction: Lab 1 – Blog Setup & Unity ML-Agents Environment"
date: 2025-10-18
description: "Setting up an online blog, configuring Unity ML-Agents, testing environments, overcoming issues, and extending the baseline scenario."
tags: ["HCI", "Unity", "ML-Agents", "Reinforcement Learning", "Lab Work"]
---

# Lab Homework 1  
*Blog Setup & Unity ML-Agents Environment*  
*Master’s in Computer Vision & AI — Gustavo*

> This post documents the full process of setting up my online blog for the course and configuring the Unity ML-Agents environment. Instead of simply presenting results, I focus on the **process**, the **problems**, and the **lessons learned**, as the lab sheet requests.

---
<!--more--> 


# 1) Lab A – Blog Setup (5 Points)

### Goal  
Create an online blog to document every lab assignment throughout the course.

### My Choice: **Hugo + GitHub Pages**

I chose **Hugo** because it is:
- lightweight and extremely fast  
- easy to deploy on GitHub Pages  
- ideal for technical writing with Markdown  
- highly customizable with themes  
- easy to maintain during the semester  

### Steps I followed

#### 1. Installing Hugo
```bash
brew install hugo
````

#### 2. Creating the blog structure

```bash
hugo new site hci-blog
```

#### 3. Adding a theme

I selected the theme **PaperMod**, which is clean, minimal, and ideal for academic posts.

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
```

Then I updated the `config.toml` to activate the theme and add metadata.

#### 4. Creating the first post

```bash
hugo new posts/lab-homework-1.md
```

#### 5. Deploying to GitHub Pages

I connected the blog to a GitHub repository and deployed with:

```bash
hugo --minify
```

The generated `public/` folder became my GitHub Pages branch.


# 2) Lab B – Unity ML-Agents Setup & Testing (10 Points)

### Goal

Install Unity, set up the ML-Agents toolkit, run the example learning environments, and validate that the reinforcement learning pipeline works locally.

### Tools Used

* **Unity 2022 LTS**
* **ML-Agents 4.0**
* Python 3.10 environment with `mlagents` installed
* Example environment: **3D Balance Ball**


# 2.1 Installing Unity & ML-Agents

### ① Installing Unity

I used **Unity Hub** to install:

* Unity 2022.3 (LTS)
* Required modules: Windows + Mac build support

### ② Installing ML-Agents Toolkit

I followed the official documentation:

[https://docs.unity3d.com/Packages/com.unity.ml-agents@4.0/manual/index.html](https://docs.unity3d.com/Packages/com.unity.ml-agents@4.0/manual/index.html)

The Python package was installed with:

```bash
pip install mlagents
pip install torch
```

### ③ Cloning the ML-Agents Repository

```bash
git clone https://github.com/Unity-Technologies/ml-agents
```

### ④ Opening the Example Project

I opened the folder `Project/` inside Unity Hub.

Unity automatically imported all ML-Agents components and environments.


# 2.2 First Test: Running “3D Balance Ball”

### What I Tested

* Agent behavior scripts
* Rewards
* Training backend (`mlagents-learn`)
* Communication between Unity ↔ Python

### Running training

Inside the Unity project folder:

```bash
mlagents-learn config/trainer_config.yaml --run-id=BalanceBallTest
```

After pressing **Play** in Unity, training successfully started.

### What I observed

* Agents gradually balanced the ball longer
* Reward curves increased steadily
* No communication errors between Unity and Python
* Training was stable with PPO


# 3) Extending the Project Idea (5 Points)

The lab asks to **extend the idea** of the existing environment to a new situation.

### My Extension: “3D Balance Ball – Wind Edition”

I modified the environment by adding:

* A **wind zone** that changes direction randomly
* A **temporary gust** effect that pushes the platform
* A **noise factor** forcing the agent to adapt more dynamically

### Why this extension is interesting

It transforms a deterministic environment into a **stochastic control task**, closer to real-world applications where actions have unpredictable outcomes.

### Expected behavior to learn

* Stronger corrective torques
* Anticipation of perturbations
* Learning a more robust policy

This extension will be useful for future reinforcement learning experiments.


# 4) Problems Encountered & How I Solved Them

### Problem 1 — Package Import Errors

When opening the ML-Agents project, Unity threw warnings about script compilation order.

**Solution:**
Reimported the folder `Packages/ML-Agents` and let Unity rebuild scripts.


### Problem 2 — Python not communicating with Unity

The console showed:

```
Unity.EnvironmentException: Couldn't connect to trainer.
```

**Solution:**

* Ensured correct Python version (3.10).
* Checked that firewall wasn’t blocking port 5004.
* Re-ran using:

```bash
mlagents-learn --env=Build/Ball.app
```


### Problem 3 — Slow training due to GPU conflicts

Torch was not detecting the GPU initially.

**Solution:**
Reinstalled PyTorch with proper CUDA support.


# 5) Recommendations for Future Students

Based on my experience, here is what I wish I knew at the start:

* **Unity versions matter** — always use LTS.
* ML-Agents requires the **right Python version** (3.10 works best).
* Don’t skip reading the **Learning Environment Examples** documentation:
  [https://docs.unity3d.com/Packages/com.unity.ml-agents@4.0/manual/Learning-Environment-Examples.html](https://docs.unity3d.com/Packages/com.unity.ml-agents@4.0/manual/Learning-Environment-Examples.html)
* Start with **Balance Ball** — it is the best debugging baseline.
* When things break (and they will), check:

  1. Python environment
  2. Unity editor console
  3. ML-Agents communication logs

Reinforcement learning pipelines are fragile; patience and incremental debugging are essential.




