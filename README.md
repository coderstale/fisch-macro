## 🎣 Fisch Auto Catcher — AI-Powered Game Assistant for Roblox

> Smart real-time object detection and automation for Roblox’s fishing mini-game “Fisch”.

⸻

# 📌 Overview

This project is a computer vision + automation tool designed for the Roblox game Fisch. The goal of the project was to track in-game elements such as the fish target marker and catch bar using YOLOv8 models, and control gameplay actions like pressing spacebar based on their relative positions — effectively automating the mini-game to always catch fish.

📂 Dataset Used:
self made dataset (included in the Kaggle Dataset Link).

⸻

# ⚙️ Features Implemented

	•	✅ YOLOv8 Training for fishTarget and catchBar
	•	✅ Multiple training attempts using yolov8n.pt and yolov8m.pt
	•	✅ Real-time screen detection using mss and OpenCV
	•	✅ Smoothing algorithms to reduce tracking flicker (Kalman Filter, exponential smoothing)
	•	✅ Tracking buffer and stability fixes for visual consistency
	•	✅ ByteTrack integration for object-level tracking across frames
	•	✅ Automation logic to press or hold the spacebar to control the catch bar
	•	✅ Reinforcement learning (RL) setup using Stable Baselines3 to learn how to press space optimally
	•	✅ Experimental ONNX model quantization for performance testing

⸻

# 🧪 How It Works

	1.	Two separate YOLOv8 models are trained:
	•	fishTargetModel to detect the target marker
	•	catchBarModel to detect the moving bar
	2.	During runtime:
	•	The screen is captured in real-time.
	•	Both models detect their respective targets.
	•	Detected positions are smoothed and stored.
	•	The center of the catch bar is compared with the position of the fish target.
	•	Based on their difference:
	•	If the fish target is right → hold space.
	•	If slightly off → tap space with intervals.
	•	If too far left → release completely.
	3.	(Experimental) An RL agent learns how to perform this better over time.

⸻

# 🛠️ Tech Stack

	•	Python 3.11
	•	Ultralytics YOLOv8
	•	Torch 2.5.1
	•	OpenCV
	•	mss (screen capture)
	•	ByteTrack (object tracking)
	•	Stable-Baselines3 (for RL)
	•	xdotool / pyautogui for automation

⸻

# ⚠️ Challenges & Roadblocks

Throughout development, several technical challenges were faced:
	•	❌ Tracking Flicker & ID Switching
Even with smoothing, object IDs would often reset when detections flickered or failed momentarily.
	•	❌ Spacebar Logic Was Inexact
The logic to hold, tap, or release spacebar couldn’t fully replicate human-like finesse — often moving too slow or overshooting.
	•	❌ Real-Time Screen + Model Inference Lag
Combining screen capture, two YOLO models, and frame rendering sometimes introduced delay.
	•	❌ Reinforcement Learning (RL) Not Trained Yet
RL setup was started using PPO but halted due to inconsistent screen shape dimensions and gym environment complexity.
	•	❌ No GPU Support in Real-Time (M1/M2)
MPS (Apple GPU) support is experimental and limited compared to CUDA.

⸻

# 🛑 Why the Project Is Paused

Despite reaching a working prototype, I decided to pause development due to:
	•	🧠 Lack of Advanced RL and Control Knowledge
The next step required strong experience in RL tuning and custom gym environment creation, which exceeded my current skill level.
	•	🧪 Automation Accuracy Wasn’t Reliable Enough
It didn’t perform perfectly in every scenario due to frame drops or missing detections.
	•	💻 Performance Limits on MacBook M4 Pro
Despite decent performance, handling two models + real-time screen capture + automation had limitations.

⸻

# 💭 Future Improvements

If resumed in the future, here’s what I’d focus on:
	•	🔁 Switch to one unified YOLO model with two classes
	•	🧠 Finish RL implementation using PPO or SAC
	•	🎮 Incorporate full game simulation with Gym
	•	💡 Make detection resolution adaptive to performance
	•	📦 Bundle as a DMG or app for one-click automation

⸻

# 🎮 Roblox Game

This tool was built specifically for the Roblox game Fisch which contains a fishing mechanic mini-game requiring timing and coordination.

It automates the reaction loop using vision + key automation.

⸻

# 📌 Dataset (Kaggle)

You can explore the dataset used for training here:
🔗 https://kaggle.com/datasets/b883f2b22ebbbf7c1f1075cadbe8ed21607a32970bfd6c4d1a619464cc9efe5a

⸻

# 📝 License

This project is for educational and experimental purposes. All rights to the original game (Fisch on Roblox) belong to its developers.

⸻

