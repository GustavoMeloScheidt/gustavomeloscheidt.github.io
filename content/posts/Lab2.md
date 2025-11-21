---
title: "Master 2 - Human Computer Interaction: Lab Homework 2 – Mobile Controls & Deployment for ML-Agents Project"
date: 2025-10-25
description: "Adapting the TrackBot reinforcement learning environment to mobile using on-screen buttons and deploying the Unity build to Android."
tags: ["Unity", "Mobile Development", "ML-Agents", "Reinforcement Learning", "HCI", "Deployment"]
---

# Lab Homework 2  
*Adapting the ML-Agents TrackBot Project to Mobile*  
*Master’s in Computer Vision & AI — Gustavo*

This lab extends the reinforcement-learning final project of this class: an RL agent (*TrackBot*) trained using Unity ML-Agents to reach a randomly placed “Goal.” 

---
<!--more-->

# 1) The agent has **three discrete actions**:

1. Move forward  
2. Rotate left  
3. Rotate right  

These actions were originally controlled on desktop by **arrow keys** (via `Heuristic()`), but this lab required adapting the interaction model to **mobile input**, where keyboard keys do not exist.

I chose moving with *three on-screen buttons* as the most appropriate mapping.  
It reflects the discrete nature of the agent and matches the logic used in the RL training.


# 2) Designing Mobile Interaction (10 Points)

## You may be asking youself: Why On-Screen Buttons?
The TrackBot only accepts *discrete* actions.  
Mobile joysticks produce continuous input, while gyroscope introduces unnecessary noise and instability.

On-screen buttons provide:

- clear affordance  
- ease of learning  
- perfect mapping to discrete actions  
- low ambiguity (important for debugging)  
- reproducibility across devices  

This matches good HCI principles: **consistency**, **match between system and real-world expectations**, and **low cognitive overhead**.


# 2.1 Creating the Mobile UI

Using Unity’s UI Toolkit (or Canvas + Buttons), I created three buttons:

- **Forward**  
- **Turn Left**  
- **Turn Right**

Each button triggers a corresponding value stored in a `mobileAction` variable.  
This action is then used inside the `Heuristic()` function of the agent.

The layout is simple:

```

[   Turn Left   ]   [ Forward ]   [   Turn Right   ]

```

Placed at the bottom of the screen, centered horizontally.


# 2.2 Implementing Mobile Input

## MobileInputController.cs
I created a small script that stores which button is currently being pressed.

```csharp
using UnityEngine;

public class MobileInputController : MonoBehaviour
{
    public int CurrentAction = 0;

    public void OnForwardPressed()
    {
        CurrentAction = 1;
    }

    public void OnLeftPressed()
    {
        CurrentAction = 2;
    }

    public void OnRightPressed()
    {
        CurrentAction = 3;
    }

    public void OnButtonReleased()
    {
        CurrentAction = 0; // no action
    }
}
```

Each UI button calls these methods through Unity’s **OnClick()** and **OnPointerDown/Up** events.


# 2.3 Connecting the Input to TrackBot

Inside **`TrackBot.cs`** (your real file ), in the `Heuristic()` method, I replaced the keyboard logic with mobile logic:

```csharp
public MobileInputController mobileInput;

public override void Heuristic(in ActionBuffers actionsOut)
{
    var discreteActionsOut = actionsOut.DiscreteActions;

    // Default: do nothing
    discreteActionsOut[0] = 0;

    // Mobile action (from UI buttons)
    if (mobileInput != null)
    {
        discreteActionsOut[0] = mobileInput.CurrentAction;
    }
}
```

This ensures:

* desktop training still works
* mobile now controls the agent
* RL logic is unchanged

This approach abstracts the input cleanly and matches the architecture expected in ML-Agents.


# 3) Deploying the Application (5 Points)

The second part of the lab was to **deploy the adapted application to a mobile device**.

I followed the official Unity documentation for Android deployment:

[https://docs.unity3d.com/Manual/android-BuildProcess.html](https://docs.unity3d.com/Manual/android-BuildProcess.html)


# 3.1 Environment Setup

In Unity Hub, I installed:

* Android Build Support
* Android SDK
* Android NDK
* OpenJDK

This step is essential, without it Unity cannot export APKs.


# 3.2 Configuring the Build Settings

In *File → Build Settings → Android*:

* Switched platform to Android
* Set resolution & presentation to portrait
* Disabled unused features for performance
* Ensured minimum API level ≥ Android 8.0


# 3.3 Deploying to Device

Steps:

1. Enabled developer mode on the phone
2. Enabled USB debugging
3. Connected phone via ADB
4. Clicked **Build & Run**

Unity compiled the APK and installed it directly on the device.


# 4) Testing the Mobile Application

After deployment, the TrackBot environment worked as expected:

* Touch buttons correctly triggered actions
* The TrackBot rotated and moved exactly like on desktop
* Rewards, collisions, and episode resets remained unchanged

The GUI debugging script (`GUI_TrackBot.cs` ) worked perfectly on mobile and was very helpful for observing:

* episode number
* step count
* cumulative reward

This helped confirm that the RL logic stayed intact.


# 5) Problems Encountered & How I Solved Them

### *Problem 1 — Button presses felt "off" (agent kept moving after releasing).*

**Cause:**
Using only `OnClick()` does not detect release.

**Fix:**
Use **OnPointerDown** and **OnPointerUp** events:

* Down → set action
* Up → return to action 0


### *Problem 2 — Touch inputs not detected in build.*

**Cause:** EventSystem missing in scene.

**Fix:**
Added:

```
GameObject → UI → EventSystem
```


### *Problem 3 — The TrackBot rotated too fast on mobile.*

**Cause:** User presses faster than keyboard repeat rate.

**Fix:**
Reduced rotation speed on mobile builds using:

```csharp
#if UNITY_ANDROID
_rotationSpeed = 120f;
#endif
```

# Conclusion

In summary: this lab was to show the transformation of the TrackBot RL experiment into a functional mobile application.

I learned:

* how to create mobile-friendly UI
* how to deploy Unity applications to Android
* how to debug mobile behavior


