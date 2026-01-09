# Engine Simulator

> **A High-Fidelity Interactive 3D Jet Engine Simulator for Aerospace Education.**

The **Engine Simulator** bridges the gap between theoretical aerospace engineering and interactive learning. Built with modern web technologies, it allows students and enthusiasts to explore complex turbo jet engine in a physics-based 3D environment.

## 🌟 Key Features

*   **Interactive 3D Models**: Inspect highly detailed 3D assets of aircraft engines. Rotate, zoom, and explode views to understand internal components.
*   **Physics-Based Simulation**: Real-time calculation of key engine parameters:
    *   **N1 / N2 Spool Speeds**
    *   **EGT (Exhaust Gas Temperature)**
    *   **Thrust & Fuel Flow**
    *   **Compression Ratios**
*   **Immersive Lab Environment**: A comprehensive 3D workshop scene illuminated by realistic lighting and dynamic camera controls.
*   **AI Academy**: A gamified learning hub featuring:
    *   Structured Chapters (Intro to Propulsion, Advanced Thermodynamics, etc.)
    *   Interactive Quizzes
    *   Virtual Mentor assistance
*   **Cross-Platform Architecture**: Designed to run seamlessly as a **Web Application** and a **Native Android App** (via Capacitor).

---

## 🏗️ Architecture Overview

The project follows a modular architecture separating the 3D rendering engine from the UI and logic layers.

### 1. The Core (3D Engine)
Located in `src/core`, the heart of the application is the **SceneManager**.
*   **Orchestration**: Manages the Three.js scene, camera, and renderer.
*   **Loop**: Handles the requestAnimationFrame loop, updating physics and rendering frames.
*   **State**: Syncs the 3D world state with the UI overlay.

### 2. The Engines
Located in `src/engines`. Each engine type (Turbofan, Turbojet, etc.) extends a base class and defines its own:
*   **Geometry**: Loading and managing GLTF/GLB assets.
*   **Animation**: GSAP timelines for spool-up/spool-down sequences.
*   **Simulation Logic**: Specific formulas for thrust and fuel consumption calculations.

### 3. The UI Layer
Located in `src/ui`.
*   **Overlay**: HTML/CSS interface floating above the 3D canvas (Canvas usually sits at z-index 0).
*   **Interactivity**: Controls for throttle, ignition, and mode switching.
*   **Responsiveness**: Adaptive layouts for mobile and desktop screens.

---

## 🚀 Getting Started

Follow this guide to set up the project locally.

### Prerequisites

Ensure you have the following installed on your machine:

*   **Node.js** (v18+ LTS recommended)
    *   Check version: `node -v`
*   **npm** (comes with Node.js)
    *   Check version: `npm -v`
*   **Android Studio** (Optional, only for mobile development)
    *   Required for building the APK.

### Installation

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/your-username/engine-simulator.git
    cd engine-simulator
    ```

2.  **Install Dependencies**
    This installs all required packages associated with Vite, Three.js, and Capacitor.
    ```bash
    npm install
    ```

---

## 💻 Running Locally

### Development Server
Start the local development server with hot-reload enabled.
```bash
npm run dev
```
*   **Local URL**: `http://localhost:5173`
*   **Network URL**: If you want to test on a mobile device connected to the same WiFi, use `npm run dev -- --host`.

### Building for Production
Create a production-ready build (minified and optimized) in the `dist/` folder.
```bash
npm run build
```
To preview the production build locally:
```bash
npm run preview
```

### 📱 Mobile Development (Android)

1.  **Sync Web Assets**
    Copy your `dist` folder to the Android native project.
    ```bash
    npm run build
    npx cap sync
    ```

2.  **Open in Android Studio**
    ```bash
    npx cap open android
    ```
    From here, you can run the app on an Android Emulator or a physical device connected via USB.

---

## 📂 Project Structure

```
c:\engine-simulator\
├── android/              # Native Android project files
├── src/
│   ├── core/             # SceneManager, DatabaseManager, EventBus
│   ├── engines/          # 3D Engine classes (Turbofan.js, etc.)
│   ├── ui/               # UI Components (HUD, Menu, Auth)
│   ├── data/             # Learning content and quiz data
│   ├── animations/       # GSAP animation controllers
│   ├── main.js           # Application entry point
│   └── style.css         # Global styles and variables
├── public/               # Static assets (images, 3D models)
├── capacitor.config.json # Capacitor configuration
└── vite.config.js        # Vite bundler configuration
```

---

## 🔧 Troubleshooting

### "Module not found" or "Vite not found"
*   **Cause**: Dependencies are not installed.
*   **Fix**: Run `npm install` again in the root directory.

### "WebGL not supported"
*   **Cause**: Your browser or graphics driver may have hardware acceleration disabled.
*   **Fix**: Update your graphics drivers or enable "Hardware Acceleration" in your browser settings.

### White Screen on Android
*   **Cause**: The web assets might not be synced, or there is a routing path issue.
*   **Fix**: Ensure you ran `npm run build` followed by `npx cap sync` before opening Android Studio.

---
FOLDER LINK:
https://drive.google.com/drive/folders/1qjzQ_RevrT9RF158RQs2qSNCphdSwdl7?usp=sharing
