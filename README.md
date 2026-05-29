# 🚜 KhetRakshak
### Contextual Edge-AI & Autonomous Rover for Crop Protection

![Kotlin](https://img.shields.io/badge/Kotlin-1.9.0-blue.svg?logo=kotlin)
![TensorFlow Lite](https://img.shields.io/badge/TensorFlow%20Lite-YOLOv11_Nano-FF6F00.svg?logo=tensorflow)
![Architecture](https://img.shields.io/badge/Architecture-MVVM-success)
![Hardware](https://img.shields.io/badge/Hardware-Custom_Rover-lightgrey)

> **The Problem:** Farmers lose billions of dollars to crop pests every year, but identifying the exact species before the infestation spreads is incredibly difficult. Spraying chemicals blindly leads to severe environmental damage, pesticide runoff, and massive financial loss. 
>
> **The Solution:** **KhetRakshak** (formerly PestAI) is a complete agricultural ecosystem. It combines a scratch-built autonomous rover for field patrolling with a real-time, edge-computing mobile app. Powered by on-device Machine Learning (YOLOv11 Nano) and dynamic weather heuristics, it acts as an entomologist in the farmer's pocket—detecting pests, recommending treatments, and advising on the exact right time to spray.

---

## 📑 Table of Contents
1. [Core Ecosystem Features](#-core-ecosystem-features)
2. [Advanced AI/ML Architecture](#-advanced-aiml-architecture)
3. [The Hardware: Autonomous Rover](#-the-hardware-autonomous-rover)
4. [Tech Stack & Architecture](#-tech-stack--architecture)
5. [Installation & Setup](#-installation--setup)
6. [Future Scope](#-future-scope)

---

## ✨ Core Ecosystem Features

### 🌦️ Spray Viability Decision Engine
* **Contextual Weather Warnings:** Issues a strict "Do Not Spray" warning if rain, high wind, or extreme temperatures are detected via the OpenWeatherMap API, preventing chemical runoff.
* **Dynamic Location Services:** Automatically requests location via the Fused Location Provider to fetch hyper-local, accurate weather data.
* **Live Agricultural Dashboard:** The home screen provides a comprehensive environmental overview—displaying current location, temperature, wind speed, and farm status before any treatment is applied.

### 💊 Remedies & Actionable Insights
* **Dedicated Remedies Screen:** Once a pest is identified, the app doesn't just leave the user hanging. It navigates to a dedicated UI offering organic and chemical treatment recommendations tailored to the specific infestation.

---

## 🧠 Advanced AI/ML Architecture

> We didn't just wrap a model in an app; we engineered a production-grade, context-aware pipeline optimized for low-end mobile hardware without relying on cloud processing.

* **Context-Aware Habitat Filter:** An intelligent heuristic filter that probes the pixels immediately outside a bounding box. If the background isn't mathematically detected as green leaves or brown soil, the model's confidence is dynamically penalized to drastically reduce false positives on unnatural surfaces.
* **Anti-Flicker Engine:** A custom 3-frame memory grace period integrated into the Non-Maximum Suppression (NMS) logic. This prevents bounding boxes from blinking in and out of existence during camera shake.
* **Active Learning Feedback Loop:** Users can tap on an incorrect bounding box to instantly hide it. The AI adds that coordinate to a "penalized zone" for the rest of the session.
* **Zero-Distortion Cropping:** Prevents 16:9 camera feeds from being squashed into 1:1 AI tensors, preserving real-world geometry for higher YOLOv11 inference accuracy.

---

## 🤖 The Hardware: Autonomous Rover

*KhetRakshak extends beyond the smartphone screen. The app is designed to pair seamlessly with our scratch-built, autonomous agricultural rover.*

* **Field Patrolling:** The rover navigates the farm, allowing the mobile system to scan vast areas of crops continuously without manual human labor.
* **Hardware-Software Synergy:** The Kotlin app acts as the brain and interface, processing the visual data captured during the rover's patrol routes.

---

## 🛠️ Tech Stack & Architecture

> The Android application utilizes modern development standards, ensuring high scalability and zero memory leaks during intensive edge-AI camera operations.

* **Language:** Kotlin
* **Architecture Pattern:** `MVVM` (Model-View-ViewModel) with a Single-Activity architecture using the `AndroidX Navigation Component`.
* **Machine Learning:** TensorFlow Lite (`YOLOv11 Nano`).
* **Asynchronous Operations:** Kotlin Coroutines and `lifecycleScope` for thread-safe API calls.
* **Camera Edge-Computing:** AndroidX `CameraX` for lifecycle-aware processing.
* **Networking:** `Retrofit` and `Gson`.
* **UI Framework:** Material Design 3, `ConstraintLayout`, and `CoordinatorLayout`.

---

## ⚙️ Installation & Setup

### Prerequisites
* Android Studio (Iguana/Jellyfish or newer)
* A physical Android device (Emulators cannot simulate the hardware acceleration required for real-time CameraX AI inference).

### Build Instructions

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/YOUR_USERNAME/KhetRakshak.git](https://github.com/YOUR_USERNAME/KhetRakshak.git)
   ```

2. **Configure API Keys:**
   * Obtain a free API key from [OpenWeatherMap](https://openweathermap.org/).
   * Do not hardcode the key. Place it securely in your `local.properties` file:
     ```properties
     WEATHER_API_KEY="your_api_key_here"
     ```

3. **Build and Run:** Sync your Gradle files and deploy the application to your connected physical device via USB debugging.

---

## 🚀 Future Scope
* **Rover Telemetry Integration:** Building a direct local communication pipeline (MQTT/Bluetooth) to view rover battery life and manual override controls directly in the Android dashboard.
* **Multi-Language Support:** Translating the Remedies Screen into regional languages to increase accessibility for local farmers.

---
> **Acknowledgments:** This project was conceptualized and scratch-built by **Team Symbiotee** during the **InnovateYou Hackathon** organized by AISSMS College of Engineering, where it successfully reached the Final Round out of 450 participating teams.
