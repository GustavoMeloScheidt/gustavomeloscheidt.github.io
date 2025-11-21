---
title: "Master 2 - Human Computer Interaction: Homework 3 – Enhancing Human Abilities through Augmented Reality"
date: 2025-10-04
description: "Ideation for interfaces that extend human perception and cognition in the age of augmented reality and building and evaluating the first prototype of Dumont, an intelligent travel planner focused on sustainability and optimization."
tags: ["HCI", "Augmented Reality","Sustainability", "Prototyping", "Human Augmentation", "UX Research"]
---

# HCI – Homework 3  
*Enhancing Human Abilities in the Age of Augmented Reality*  
*Master’s in Computer Vision & AI — Gustavo*

> This exercise focuses on how **Augmented Reality (AR)** can be used to **extend human capabilities** — perceptual, cognitive, and physical.  
> Following the three-step design cycle (Ideate → Prototype → Evaluate), I developed and tested concepts that merge digital augmentation with everyday human experience.

---
<!--more-->


## 1) Lecture 7 – Ideate (5 Points)

### Goal
To explore **three AR-based ideas** that enhance specific human abilities while remaining ethical, usable, and socially acceptable.

### **Idea 1 — AR Focus Lens**
> *Helping people maintain attention and manage distractions.*

**Problem:**  
In a hyper-connected environment, attention is fragmented. Notifications, multitasking, and external stimuli degrade deep focus.

**Concept:**  
An AR headset (or phone-based AR app) that **dynamically blurs or dims** irrelevant visual elements in the environment during focused tasks.  
The system detects what the user is concentrating on (e.g., a book, laptop, or whiteboard) and **softly masks unrelated objects** using depth and gaze tracking.

**Human ability enhanced:**  
- Sustained **attention** and **mental focus**  
- Reduction of **cognitive load**  

**Sketch:**  
![Idea 1 – AR Focus Lens](/assets/AR_focus_lens.png)

**Future potential:**  
Could integrate with EEG sensors or smartwatch data to detect distraction patterns in real time.


### **Idea 2 — AR Empathy Mirror**
> *Visualizing emotions to improve interpersonal understanding.*

**Problem:**  
Humans often misinterpret others’ emotions due to lack of nonverbal sensitivity, especially in cross-cultural or digital contexts.

**Concept:**  
An AR overlay (via smart glasses) that reads facial micro-expressions, tone of voice, and body posture, and **displays emotional cues** — e.g., “nervous,” “confident,” “tired” — as subtle color halos or icons around the person.

**Human ability enhanced:**  
- **Emotional intelligence** and **empathy**  
- Support for **social learning** and **therapy**

**Ethical considerations:**  
Requires **privacy safeguards** and user consent. The system should prioritize **self-awareness** training, not surveillance.

**Sketch:**  
<img src="/assets/AR_empathy_mirror.png"
     alt="Idea 2 – AR Empathy Mirror"
     style="height:700px; width:auto;" />


### **Idea 3 — AR Time Perception Assistant**
> *Making the invisible dimension of time perceptible.*

**Problem:**  
People struggle with abstract temporal awareness — how much time they spend on tasks, or how long until an event occurs.

**Concept:**  
An AR interface that **projects time visually in the environment**.  
Example: colored rings shrinking as deadlines approach, or subtle visual indicators floating above tasks representing urgency or duration.

**Human ability enhanced:**  
- **Temporal awareness** and **self-regulation**  
- Encourages mindful use of time rather than reactive multitasking

**Sketch:**  
<img src="/assets/AR_perception_assistant.png"
     alt="Idea 3 – AR Time Perception Assistant"
     style="height:600px; width:auto;" />

**Future integrations:**  
Could sync with calendar, to-do apps, or heart rate to modulate visualization intensity during stressful periods.


## **Lecture 8 – Prototype (5 Points)**

### Goal
Build a prototype that is detailed enough to communicate the concept and allow for **first user interaction**.

### Prototype Type
For this stage, I developed a **mid-fidelity digital prototype** in **Figma**, representing the main user flow of DUMONT Planner:

1. **Input phase:** user selects origin, destination(s), and travel dates.  
2. **Processing phase:** the app compares transport modes (plane, train, bus) to compute the **cheapest**, **fastest**, and **greenest** routes.  
3. **Output phase:** DUMONT visualizes three itineraries with corresponding CO₂ emissions, travel time, and cost.  

The interface includes a clean, minimal layout emphasizing **eco-feedback** (via color-coded emissions indicators) and **decision simplicity**.

![DUMONT Prototype Sketch](/assets/DumontPlannerDemo.mov)

### Interaction Concept
The prototype supports **mixed decision criteria**, allowing users to toggle between:
- “Cheapest route”
- “Fastest route”
- “Lowest CO₂ route”

A **dynamic comparison card** highlights trade-offs, encouraging reflection about sustainable choices.  


## **Lecture 9 – Use the Prototype for Evaluation (5 Points)**

### Evaluation Setup
I conducted a test with one participant (a frequent traveler).  
The participant interacted with the clickable prototype while I simulated the backend logic (CO₂ calculations and sorting).

### Observations
- The participant was quick to understand the goal of balancing sustainability and travel convenience.  
- However, they expected more **personalization**, e.g., suggestions based on previous trips or emission targets.  
- The **color legend (green/yellow/red)** for CO₂ was intuitive but sometimes overlapped with cost indicators, creating minor confusion.  
- The user appreciated the **transparency** (“I can see the environmental impact of my decision”), suggesting a sense of **ethical empowerment**.

### Reflections
This first evaluation validated the core concept — users want to make **eco-informed travel choices** but still need clarity in how trade-offs are presented.  
In the next iteration, I plan to:
1. Simplify visual hierarchy (separate CO₂ and cost indicators).  
2. Introduce **interactive sliders** to adjust preference weights between cost, time, and emissions.  
3. Provide **feedback on cumulative impact** (e.g., total CO₂ saved per year).



### **Conclusion**
The prototype successfully achieved **first-user exposure**, confirming that sustainability and usability can coexist in travel planning.  
The evaluation highlighted the importance of **clear affordances** and **balanced feedback**, reinforcing the need to align eco-awareness with effortless decision-making.
