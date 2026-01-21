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
