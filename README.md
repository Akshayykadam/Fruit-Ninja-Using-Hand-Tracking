# 🍉 Fruit Ninja - Hand Tracking Edition

A reimagined version of the classic Fruit Ninja game, powered by **MediaPipe** for real-time hand tracking. Slice fruits with your hands using just a webcam!

![Unity](https://img.shields.io/badge/Unity-2021.3+-black?logo=unity)
![MediaPipe](https://img.shields.io/badge/MediaPipe-0.16.3-blue)
![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20iOS%20%7C%20Editor-green)

---

## ✨ Features

- **👋 Intearctive Hand Tracking**: Your hand is the blade! Slice through fruits using advanced hand landmark detection.
- **🍎 Classic Gameplay**: Slice watermelons, oranges, and more while avoiding bombs.
- **🔥 Visual Effects**: satisfying slice effects, particle systems, and dynamic UI.
- **📱 Cross-Platform**: Optimized for both Mobile (Android/iOS) and Desktop (Editor/Standalone).

---

## 🚀 Getting Started

### Prerequisites

- **Unity 2021.3** or later (LTS recommended).
- **Webcam** (for Editor/Desktop play).
- A mobile device (Android/iOS) for mobile deployment.


### Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/Fruit-Ninja-Using-Hand-Tracking.git
   ```

2. **Open in Unity**
   - Launch Unity Hub.
   - Add/Open the project folder.

3. **Install Dependencies**
   - The project uses the **MediaPipe Unity Plugin**. Ensure all package dependencies are resolved via the Unity Package Manager.

### 📱 Android Build Settings (Important!)

To ensure the hand tracking runs on the GPU, you **must** configure the Graphics API:

1. Go to `Project Settings > Player > Android > Other Settings`.
2. Uncheck `Auto Graphics API`.
3. **Remove** `Vulkan` (MediaPipe GPU does not support Vulkan).
4. Add `OpenGLES3` to the list.
5. Set **Minimum API Level** to `Android 7.0 (Nougat)` or higher.

### How to Play

1. Open the main scene: `Assets/FruitNinja/Scenes/FruitNinja.unity`.
2. Press **Play** in the Unity Editor.
3. Allow camera access if prompted.
4. Stand back so your hands are visible to the webcam.
5. Move your hand to slice the fruits appearing on the screen!
   - **Slice Fruits**: Earn points.
   - **Avoid Bombs**: Slicing a bomb ends the game (or reduces lives).
   - **Don't drop fruits**: Missed fruits may cost you a life.


---

## 🖐️ How Hand Tracking Works

The system uses **MediaPipe Pose** to turn your hands into virtual blades. Here is the technical breakdown:

### 1. Detection Logic
The `HandSliceController` tracks specific landmarks on your body:
- **Wrists** (Indices 15 & 16)
- **Index Fingers** (Indices 19 & 20)

A "Hand Center" is calculated by interpolating between the wrist and index finger to create a stable point that represents your hand position on screen.

### 2. Slicing Physics
To feel realistic, we don't just track position — we track **speed**:
- **Velocity Threshold**: The system acts like a real sword. It only registers a "slice" if your hand is moving faster than `300 pixels/second`. Slow movements won't cut fruit!
- **Collision**: We convert your 2D screen coordinates into Unity World Coordinates and use `Physics2D.OverlapCircle` to detect when your "hand point" intersects with a Fruit collider.

### 3. Visual Smoothing
Raw tracking data can be jittery. We use `Vector3.SmoothDamp` to interpolate the movement of the visual trails, ensuring the glowing slice effects look fluid and responsive.

---

## 📁 Project Structure

```
Fruit-Ninja-Using-Hand-Tracking/
├── Assets/
│   ├── FruitNinja/            # Main Game Assets
│   │   ├── Scenes/            # Game Scenes (FruitNinja.unity)
│   │   ├── Scripts/           # Game Logic (Spawning, Slicing, Score)
│   │   ├── Prefab/            # Fruit & Bomb Prefabs
│   │   └── UI/                # Game UI Elements
│   ├── PoseLandmarkSDK/       # Hand Tracking Core (MediaPipe implementation)
│   └── StreamingAssets/       # MediaPipe Models
```

---

## 🛠️ Technical Details

This project leverages a custom **Pose/Hand SDK** wrapper around MediaPipe to provide:
- **GPU Acceleration**: Efficient inference on mobile devices.
- **Smooth Tracking**: Filtered landmark data for stable slicing interactions.
- **Unity Integration**: Maps 2D hand coordinates to Unity World Space for interaction with 3D/2D game objects.

### key Scripts
- `HandSliceController.cs`: Manages hand input and collision detection with fruits.
- `FruitGameController.cs`: Controls the game loop, spawning logic, and state management.
- `ScoreManager.cs`: Handles scoring and UI updates.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- **MediaPipe** by Google for the incredible tracking technology.
- **Homuler** for the [MediaPipe Unity Plugin](https://github.com/homuler/MediaPipeUnityPlugin).
