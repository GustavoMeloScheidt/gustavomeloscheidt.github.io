---
title: "Master 2 - Human Computer Interaction: Homework 1 – Affordances, Gestalt Laws & Dark Design Patterns"
date: 2025-09-20
description: "Exploring how design communicates action possibilities, visual grouping principles, and the ethics of user manipulation."
tags: ["HCI", "Affordances", "Gestalt", "Dark Patterns"]
---

# HCI – Homework 1  
*Affordances, Gestalt Laws, and Dark Patterns*  
*Master’s in Computer Vision & AI — Gustavo*

> In this post, I document **real examples** (both physical and digital) from my daily life, explain why they work or fail according to HCI principles, and propose **practical redesigns**.  

---
<!--more-->


## 1) Affordances (5 pts)

### Understanding the concept
- **Affordance**: the possible actions suggested by the properties of an object (Norman).  
- **Signifier**: a perceptible cue that communicates the affordance.  
- **Mapping & Feedback**: the relation between control and its effect; how the system responds after the action.


### 1.1. **Good Affordance** — Brightness Slider on iPhone (or Android)  
*(digital — with feedback)*

![Good Affordance – Brightness Slider](/assets/control_brightness.png)

**Why it’s good**
- The **vertical shape** and **light–dark gradient** clearly **indicate “drag up/down for brightness”** (strong visual signifiers).  
- The **mapping** is natural (up = more brightness).  
- The **feedback** is **immediate and continuous** — the screen responds in real-time to user input.

**Design insights**
- Relies on **cultural conventions** (up = increase).  
- Minimizes cognitive load: no textual explanation needed, the **visual itself** conveys the action.


### 1.2. **Bad Affordance** — A Double door with Conflicting Cues
*(physical — classic “Norman Door” example)*

![Bad Affordance – Misleading Door](/assets/door_horizontal_bar.jpg)
<!--[Source](https://medium.com/@nzim01/its-push-not-pull-the-engineering-building-door-dilemma-dd65143396f4)-->
<p align="center">
  <a href="https://medium.com/@nzim01/its-push-not-pull-the-engineering-building-door-dilemma-dd65143396f4">
    Source
  </a>
</p>

**Why it’s bad**  
- Both doors use **vertical pull handles** on **both sides**, visually affording *pulling* even when the correct action is *pushing*.  
- The design violates the **principle of mapping** — the handle shape does not correspond to the intended movement.  
- The **feedback** (door resistance) only appears *after* a failed action, causing confusion and repeated errors.  
- The glass surface gives **no visible hinge cues**, making it hard to infer direction of motion.

**How to fix it**  
1. Use **flat push plates** on the push side to clearly signal the action.  
2. Keep **vertical handles only on the pull side**.  
3. Add **concise, redundant text labels** (“PUSH / PULL”) in contrasting typography.  
4. Ensure **visible hinges or pivot details** to communicate motion direction.  
5. Optionally, use **tactile or visual feedback** (like a small light indicator) to confirm the door is unlocked.


## 2) Gestalt Laws (5 pts)

> Below are **two real-life examples** (one physical, one digital) where Gestalt principles were violated, creating confusion — and how to fix them.


### 2.1. **Misaligned Price Tags in a Supermarket**  
*(physical — proximity, alignment, and common region)*

> ![Gestalt – Misaligned Price Tags](/assets/misaligned_labels.jpg)

**What went wrong**
- Price labels are superposing each other.
- The **horizontal proximity** suggests a wrong pairing.  
- Lack of **vertical alignment** breaks **continuity** — our brain expects columns to flow smoothly.

**How to fix it**
- Create **product cards** where **item and price** share the same **visual region** (common region).  
- **Align prices** to the **center of the product**, not to shelf dividers.  
- Add **redundant cues**: small product photo or SKU printed on the tag.  
- Ensure **clearer spacing** between product groups to strengthen **proximity grouping**.


### 2.2. **Confusing Bus Schedule Table**  
*(digital — similarity, proximity, and color-only distinction)*

<img src="/assets/bus_schedule.jpg"
     alt="Gestalt – Confusing Schedule Table"
     style="height:600px; width:auto;" />


**What went wrong**  
- Multiple **routes (A, B, D, R)** are distinguished **only by color**, violating both **redundancy** and **color accessibility** principles.  
- The **dense layout** and **tight proximity** between rows make it difficult to identify which times belong to each route.  
- Lack of **clear region separators** (for cities, stops, or direction) causes visual overload and misgrouping.  
- The **alignment of text and numbers** changes subtly between columns, breaking the law of **continuity** and increasing cognitive load.

**How to fix it**  
- Use **textual identifiers** (A, B, D, R) alongside **shapes or icons** for redundant encoding and not color alone.  
- Introduce **horizontal spacing** or **light dividing lines** between route groups to reinforce **common region**.  
- Highlight **major stops** with subtle background shading or icons to help navigation.  
- Keep **sticky headers** for each route (when scrolling digitally) to preserve context.  
- Apply **consistent alignment** and grid structure so users can easily scan and compare times.


## 3) Dark Design Patterns (5 pts)

> Here I discuss **two dark patterns** that I often encounter and propose **ethical redesigns** with the opposite intention.

### 3.1. **Forced Continuity** — “Free trial” that auto-renews  
**Scenario:** A 7-day free trial that requires a credit card, hides the cancellation option, and charges automatically.

**Why it’s dark**
- Exploits **inertia bias** and **forgetfulness**.  
- Violates **informed consent**: pricing and cancellation paths are intentionally unclear.

**Redesign (ethical opposite)**
1. **Double opt-in** before charging: notify the user before renewal and ask for explicit confirmation.  
2. **Symmetric cancellation**: as easy to cancel as it was to subscribe.  
3. **Transparent pricing summary** above the confirmation button.  
4. **Visible billing info** (next payment date) in the user dashboard.  
5. Shift company KPIs from **“retention by confusion”** to **“retention by satisfaction.”**


### 3.2. **Confirmshaming** — Shaming the user for saying “no”  
**Example:** Popup: *“Do you want 10% off?”* with buttons:  
- “Yes, I love saving money!”  
- “No, I like paying full price.”

**Why it’s dark**
- Uses **emotional manipulation** to push compliance.  
- Creates guilt and pressure — unethical persuasive design.

**Redesign (ethical opposite)**
1. Use **neutral language**: “Would you like to receive email offers?”  
   Buttons: **“Yes, subscribe” / “Not now.”**  
2. Allow **granular preferences** (frequency, categories).  
3. Make **unsubscribe links** clear and one-click.  
4. Default to **no subscription** if the popup is closed — **no trick consent**.

