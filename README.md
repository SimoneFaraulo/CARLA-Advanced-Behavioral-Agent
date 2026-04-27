# 🚗 CARLA Cognitive Navigation System
> An advanced, highly modular behavioral agent for the CARLA Simulator featuring a Chain of Responsibility architecture for safe urban navigation.

![CARLA Simulator](https://img.shields.io/badge/CARLA-0.9.10+-blue.svg)
![Python](https://img.shields.io/badge/Python-3.7+-yellow.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

This repository contains the final project for the **Autonomous and Connected Vehicles (2025/2026)** course at the University of Salerno. Our goal was to design, implement, and test an autonomous driving agent capable of proactive decision-making, strict adherence to traffic rules, and dynamic obstacle evasion within the CARLA simulator.

---

## ✨ Key Architectural Features

Unlike traditional monolithic approaches, our agent relies on a highly scalable, modular infrastructure. The system transitions the vehicle from a passive actor into a **proactive, context-aware agent** through two main architectural pillars:

### 1. The "Chain of Responsibility" (CoR) Cognitive Pipeline
We implemented a rigid hierarchy of independent `Evaluators` that process environmental data. If a module detects a critical situation, it generates a control command and interrupts the chain; otherwise, it passes control to the next module. 
* 🚦 **Traffic Signal Evaluator**: Strict adherence to traffic lights.
* 🚶‍♂️ **Pedestrian Evaluator**: Dynamic scanning and emergency braking for vulnerable road users.
* 🛑 **Stop Sign Evaluator**: Accurate distance calculation and mandatory halting at intersections.
* 🚧 **Static Obstacle Evaluator**: Detection of hazards (e.g., cones, warning signs) and calculation of safe lateral offsets.
* 🚗 **Traffic Proximity & Cruise Evaluators**: Adaptive Cruise Control (ACC) and standard lane following.

### 2. Tactical Execution Engines
When standard lane following is not enough, long-term spatial planning is handed over to specialized tactical engines:
* **Intersection Navigation Engine**: Uses advanced topological and vector analysis to map junctions and negotiate right-of-way safely.
* **Overtaking Engine**: Employs real footprint calculation (using Convex Hull) and kinematics to execute dynamic evasive maneuvers and overtakes, even accounting for oncoming traffic.

---

## 📊 Simulation Results

The agent was rigorously tested using the CARLA Leaderboard evaluation framework. We compared our architecture against a baseline behavioral agent, achieving unprecedented improvements in both safety and completion metrics.

### 📍 Route 1 (Standard Urban Traffic)
* **Baseline:** Failed to complete the scenario due to severe timeouts and inability to bypass static environmental hazards.
* **Our Agent:** Achieved **100% Route Completion**. The agent successfully performed dynamic bypass maneuvers around static obstacles without any human intervention, avoiding timeouts and maintaining a smooth traffic flow.

### 📍 Route 4 (Highly Critical & Complex Intersections)
* **Baseline:** Demonstrated critical failures in respecting right-of-way and STOP signs, resulting in multiple collisions with pedestrians and vehicles. The Global Driving Score plummeted to a failing **2.58**.
* **Our Agent:** Completely eliminated collisions with pedestrians and vehicles. It successfully negotiated complex intersections, correctly yielding to traffic and stopping at required signs. The Global Driving Score surged to an absolute excellence threshold of **93.2**.

---

## 👥 Authors (Group 03)
* **Apicella Antonio** 
* **Cipriano Ivan Luigi** 
* **Faraulo Simone** 
* **Graziosi Antonio**

> *University of Salerno - Master's Degree in Computer Engineering*
