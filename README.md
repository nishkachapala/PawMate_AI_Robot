PAWMATE AI: TECHNICAL SYSTEM SPECIFICATION


PROJECT THEME OVERVIEW

PawMate AI implements an embodied, pet-like robotic home companion designed to assist individuals with home automation, visual monitoring, and personalized task management. Unlike standard, static smart-home hubs, it bridges the gap between human-robot interaction and autonomous safety engineering. The system features a playful, canine-like persona to build trust, uses a decoupled multi-agent setup to separate tasks, and enforces absolute safety limits that override any AI-generated movement plans.

SYSTEM ARCHITECTURE

SafetyModule: A deterministic validation layer that intercept and inspects all movements and camera requests against strict physical limits before they reach the hardware.

RobotSimulator: Handles virtual 2D planar robot kinematics (X, Y, and heading angle) and simulates real-time front-facing ultrasonic obstacle detection.

CoordinatorAgent: Powered by Gemini 2.5 Flash, it parses user commands into structured JSON to route tasks to specialized sub-agents.

MemoryDatabase: A local SQLite database that stores user preferences and stages reminders as pending approval until confirmed by the user.

VisionSystem: Uses a pretrained YOLOv8 Nano model to detect, label, and locate everyday household objects within camera frames.

CORE TECHNICAL FEATURES

Structured Intent Routing: Processes natural language commands and separates motion controls from general chat.

Embodied Pet Persona: Employs natural dialogue and local speech synthesis with integrated behavioral animal cues.

Computer Vision Surveillance: Detects and tracks household items using real-time deep learning.

Active Obstacle Avoidance: Stops the robot automatically if front-facing proximity sensors report an obstacle.

Independent Emergency Stop: Instantly kills all motor systems if safety keywords like stop or halt are triggered.

User-Approved Memory: Saves personal details and screens reminders through a safety-gated SQLite manager.

KEY RESEARCH INSIGHTS

Hybrid Routing: Incorporates hardcoded fallback rules to ensure the robot remains operational and safe even if the generative AI model hallucinates or times out.

Decoupling: Separating dialogue, vision processing, and physical navigation into independent modules reduces latency and keeps prompt token costs low.

Asynchronous Gating: Requires manual user authorization for robot actions to prevent unauthorized system operations.

Cloud Virtualization: Utilizes browser-native JavaScript bridges and lightweight web frameworks to run complex computer vision and audio tasks smoothly on standard laptops and sandbox VMs.
