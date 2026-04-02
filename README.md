# AI-Pose-Estimation
A computer-vision-based sports analytics tool designed to quantify football kicking mechanics. This project uses **MediaPipe Pose** to track knee flexion angles, detect backswing depth, and count valid kicks with a robust state-machine logic.

## 🌟 Key Features

* **Smart Activation**: Requires a stable full-leg view (Hip, Knee, Ankle) for 30 consecutive frames to activate, filtering out background noise and partial detections.
* **Backswing (Loading) Analysis**: Automatically captures the minimum knee angle during the backswing phase, a critical metric for shot power.
* **Biomechanical State Machine**: Processes movements through `READY -> BACKSWING -> KICK_COMPLETE` stages to ensure high-accuracy counting.
* **Real-time Feedback**: Live UI overlay displaying kick counts, the loading depth of the last kick, and system status.

## 📸 Demo

| 1. System Alignment | 2. Backswing Detection | 3. Kick Analysis |
| :---: | :---: | :---: |
| ![Aligning](demo/00.jpg) | ![Backswing](demo/01.jpg) | ![Kick Complete](demo/02.jpg) |
| *Waiting for 30-frame stability* | *Capturing peak flexion (loading)* | *Auto-counting & quality metrics* |

## 🚀 How It Works

### Biomechanical Thresholds
The system is calibrated based on standard football kinematics:
* **Activation**: Landmark Visibility > 0.7 (ensures full leg is in frame).
* **Backswing Stage**: Knee Angle < 110° (detects the loading phase).
* **Impact Stage**: Knee Angle > 160° (detects the leg extension).
