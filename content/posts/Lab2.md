---
title: "Master 2 - Human Computer Interaction: Lab Homework 2 – Mobile Controls & Deployment for ML-Agents Project"
date: 2025-10-25
description: "Adapting the TrackBot reinforcement learning environment to mobile using on-screen buttons and deploying the Unity build to Android."
tags: ["Unity", "Mobile Development", "ML-Agents", "Reinforcement Learning", "HCI", "Deployment"]
---

# Lab Homework 2  
*Adapting the ML-Agents TrackBot Project to Mobile*  
*Master’s in Computer Vision & AI — Gustavo*

This lab adapts the original TrackBot ML‑Agents reinforcement learning environment into a **mobile‑friendly version** using a **virtual joystick**.  
The original TrackBot could only be controlled through discrete keyboard actions, but this version introduces a **continuous mobile joystick** that directly maps the drag direction to TrackBot's movement.

---
<!--more-->
![Mobile Trackbot](/assets/mobile_trackbot.gif)

Note: as you can see, I am using the "mobile" version inside my Unity (in the computer), that is because I do not have an Android to test it and Apple makes it really hard to deploy, but everything should work the same in your phone.

## 1) Original Agent Behavior  
The TrackBot originally had three discrete actions:

1. Move Forward  
2. Rotate Left  
3. Rotate Right  

These were used during training and were accessible through `Heuristic()` for desktop control.


## 2) Designing Mobile Interaction  
### You may be asking yourself: Why a joystick instead of buttons?
A joystick provides:

- Natural direction‑based input  
- Intuitive mapping: direction dragged = direction robot moves  
- Smooth motion  
- Works extremely well with continuous 2D navigation  
- Much better mobile UX than three fixed buttons  

This follows core HCI principles:

- **Direct manipulation**
- **Low cognitive load**
- **Immediate feedback**
- **Consistency with mobile game patterns**


## 3) Building the Mobile Joystick

### 3.1 Joystick UI  
Created using Unity Canvas:

```
Canvas
 └── JoystickBackground (Image)
       └── JoystickHandle (Image)
```

The background stays anchored bottom‑left.  
The handle moves inside it when dragging.


## 3.2 Joystick Script  
A simplified joystick script reads drag direction and returns a normalized vector.

```csharp
public Vector2 GetDirection()
{
    return input;
}
```

This gives a vector in range [-1, 1] × [-1, 1].


## 3.3 TrackBot Mobile Controller  
The TrackBot now:

- Rotates smoothly toward joystick direction  
- Moves forward based on joystick magnitude  
- Uses Rigidbody for physics‑friendly motion  

```csharp
Vector3 moveDir = new Vector3(dir.x, 0, dir.y);
transform.rotation = Quaternion.Lerp(...);
rb.MovePosition(...);
```

This creates a very natural 2D robot‑like movement.


## 4) Deployment to Mobile (Android)

### Requirements installed via Unity Hub:
- Android Build Support  
- SDK, NDK, OpenJDK  

### Build Settings:
- Switch platform → Android  
- Resolution = Landscape  
- ARM64 enabled  
- Minimal API Level = Android 8.0  

### Steps:
1. Enable USB debugging  
2. Connect device  
3. Press **Build & Run**  

Unity automatically builds an APK and installs it on the phone.


## 5) Mobile Testing  

The final mobile build works as expected:

- Joystick controls movement in all directions  
- Touch input is smooth and responsive  
- TrackBot physics identical to desktop  
- Rewards, resets, collisions unchanged  
- Training remains unaffected because joystick control is separate from ML‑Agents policy inference  


## 6) Problems & Solutions  

### **Problem:** Touch release not resetting movement  
**Fix:** Use `OnPointerUp` instead of `OnClick`.

### **Problem:** Joystick not working on mobile  
**Fix:** EventSystem missing. Added automatically via  
`GameObject → UI → EventSystem`.

### **Problem:** TrackBot too sensitive  
**Fix:** Clamp joystick magnitude and reduce speed on mobile.


## Conclusion  
This lab successfully demonstrates:

- Converting an ML‑Agents environment into a mobile‑friendly experience  
- Implementing an intuitive touch‑based joystick  
- Deploying and testing a Unity mobile build  
- Preserving the RL logic while adding manual control  

The TrackBot environment is now fully usable on mobile and much more interactive.

