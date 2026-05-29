🚜 KhetRakshak: Contextual Edge-AI & Autonomous Rover for Crop Protection
Farmers lose billions of dollars to crop pests every year, but identifying the exact species before the infestation spreads is incredibly difficult. Spraying chemicals blindly leads to severe environmental damage, pesticide runoff, and massive financial loss.

KhetRakshak (formerly PestAI) is a complete agricultural ecosystem that solves this. It combines a scratch-built autonomous rover for field patrolling with a real-time, edge-computing mobile app. Powered by on-device Machine Learning (YOLOv11 Nano) and dynamic weather heuristics, it acts as an entomologist in the farmer's pocket—detecting pests, recommending treatments, and advising on the exact right time to spray.

📑 Table of Contents
Core Ecosystem Features

Advanced AI/ML Architecture

The Hardware: Autonomous Rover

Tech Stack & Architecture

Installation & Setup

Future Scope

Acknowledgments

✨ Core Ecosystem Features
🌦️ Spray Viability Decision Engine
Contextual Weather Warnings: Issues a strict "Do Not Spray" warning if rain, high wind, or extreme temperatures are detected via the OpenWeatherMap API, preventing chemical runoff.

Dynamic Location Services: Automatically requests location via the Fused Location Provider to fetch hyper-local, accurate weather data.

Live Agricultural Dashboard: The home screen provides a comprehensive environmental overview—displaying current location, temperature, wind speed, and farm status before any treatment is applied.

💊 Remedies & Actionable Insights
Dedicated Remedies Screen: Once a pest is identified, the app doesn't just leave the user hanging. It navigates to a dedicated UI offering organic and chemical treatment recommendations tailored to the specific infestation.

🧠 Advanced AI/ML Architecture
We didn't just wrap a model in an app; we engineered a production-grade, context-aware pipeline optimized for low-end mobile hardware without relying on cloud processing.

Context-Aware Habitat Filter: An intelligent heuristic filter that probes the pixels immediately outside a bounding box. If the background isn't mathematically detected as green leaves or brown soil, the model's confidence is dynamically penalized to drastically reduce false positives on unnatural surfaces.

Anti-Flicker Engine: A custom 3-frame memory grace period integrated into the Non-Maximum Suppression (NMS) logic. This prevents bounding boxes from blinking in and out of existence during camera shake, providing a highly stable UX.

Active Learning Feedback Loop: Users can tap on an incorrect bounding box to instantly hide it. The AI adds that coordinate to a "penalized zone" for the rest of the session, preventing the same false-positive from recurring.

Zero-Distortion Cropping: Prevents 16:9 camera feeds from being squashed into 1:1 AI tensors, preserving real-world geometry for higher YOLOv11 inference accuracy.

🤖 The Hardware: Autonomous Rover
KhetRakshak extends beyond the smartphone screen. The app is designed to pair seamlessly with our scratch-built, autonomous agricultural rover.

Field Patrolling: The rover navigates the farm, allowing the KhetRakshak mobile system to scan vast areas of crops continuously without manual human labor.

Hardware-Software Synergy: The Kotlin app acts as the brain and interface, processing the visual data captured during the rover's patrol routes.

🛠️ Tech Stack & Architecture
We recently refactored the entire Android application to adhere to modern development standards, ensuring high scalability and zero memory leaks during camera operations.

Language: Kotlin

Architecture Pattern: MVVM (Model-View-ViewModel) paired with a Single-Activity architecture using the AndroidX Navigation Component and Fragments.

Machine Learning: TensorFlow Lite (custom-trained YOLOv11 Nano).

Asynchronous Operations: Kotlin Coroutines and lifecycleScope for thread-safe background API calls.

Camera Edge-Computing: AndroidX CameraX for a lifecycle-aware camera implementation that survives screen rotations gracefully.

Networking: Retrofit and Gson for API communication.

UI Framework: Material Design 3, ConstraintLayout, and CoordinatorLayout.

⚙️ Installation & Setup
Clone the repository:

Bash
git clone https://github.com/YOUR_USERNAME/KhetRakshak.git
Open in Android Studio: Ensure you have the latest stable version (Iguana/Jellyfish or newer) installed.

Configure API Keys: * Obtain a free API key from OpenWeatherMap.

Do not hardcode the key. Place it securely in your local.properties file:

Properties
WEATHER_API_KEY="your_api_key_here"
Build and Run: Connect a physical Android device via USB debugging. Note: Emulators are not recommended as they cannot simulate the hardware acceleration required for real-time CameraX AI inference.

🚀 Future Scope
Rover Telemetry Integration: Building a direct local communication pipeline (MQTT/Bluetooth) to view rover battery life and manual override controls directly in the Android dashboard.

Multi-Language Support: Translating the Remedies Screen into regional languages to increase accessibility for local farmers.

🏆 Acknowledgments
This project was conceptualized and scratch-built by Team Symbiotee during the InnovateYou Hackathon organized by AISSMS College of Engineering, where it successfully reached the Final Round out of 450 participating teams.
