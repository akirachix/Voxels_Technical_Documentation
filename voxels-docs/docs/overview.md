# Mara Guard Overview

## 1. About Mara Guard

**Mara Guard** is a technology-driven wildlife monitoring and early-warning system designed to help reduce human-lion conflict in the Maasai Mara. The system combines IoT hardware, artificial intelligence, wireless communication, backend services, and user-facing applications to detect and monitor lion activity.

Mara Guard provides rangers with timely information about lion activity and system status while supporting an automated local response when a lion is detected.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## 2. Problem Statement

Human-lion conflict is a challenge in areas where wildlife habitats overlap with communities, livestock, and human activity. Detecting lion activity early enough to support an appropriate response can be difficult, particularly across large and remote areas.

Traditional monitoring approaches can depend heavily on human observation and may not provide continuous automated detection. Mara Guard addresses this challenge by combining automated movement detection, AI-based image analysis, local deterrence mechanisms, and wireless communication.

The system is designed to support earlier awareness of potential lion activity and provide rangers with information that can assist with monitoring and response.

**Research Report:** [View the Mara Guard Research Report](https://docs.google.com/document/d/1KtRf4HMrOVRyFMdj8ziPap_G-VfaRBrSdqtINIzUhoQ/edit?tab=t.0#heading=h.d3jjdv9738ml)

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## 3. Target Users

### 3.1 Primary Users

**Rangers** are the primary users of Mara Guard. They use the system to monitor lion activity, view detection information, receive relevant alerts, and monitor the status of field equipment.

### 3.2 Technical Users

The technical documentation also supports team members responsible for developing and maintaining Mara Guard, including:

* Frontend developers
* Backend/API developers
* Mobile developers
* IoT and embedded developers
* AI/ML developers
* DevOps and infrastructure engineers
* New team members joining the project

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## 4. Key Features

Mara Guard provides the following core capabilities:

* **Movement Detection** — Detects movement in monitored areas using field sensors.
* **Lion Detection** — Uses the YOLOv8 artificial intelligence model to identify lions.
* **Local Deterrence** — Activates connected deterrence devices such as a spotlight and horn when a lion is detected.
* **Wireless Communication** — Transmits relevant information between field devices and the gateway using LoRa.
* **Gateway Connectivity** — Uses ESP32 and Wi-Fi to connect field information to the wider system.
* **MQTT Messaging** — Enables communication between connected system components.
* **Backend API** — Receives and provides system data to user-facing applications.
* **Data Storage** — Stores relevant detection and system information.
* **Ranger Dashboard/PWA** — Provides rangers with monitoring information.
* **Mobile Application** — Provides supported Mara Guard functionality through a Flutter application.
* **Battery Monitoring** — Provides visibility into the power status of field equipment.
* **Historical Information** — Supports review of previously recorded system information.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## 5. Workflow Overview

At a high level, Mara Guard detects movement in monitored areas and uses camera-based artificial intelligence to determine whether a lion is present. When a lion is detected, the system can activate a local deterrence response while relevant detection and system information is transmitted for storage and monitoring.

Rangers can then access the available information through the Mara Guard dashboard and mobile application.

For the detailed system workflow and data flow, see **How It Works**.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## 6. Mara Guard Objectives and Success Metrics

Mara Guard aims to improve early awareness of lion activity, support timely ranger response, and provide reliable monitoring of field operations.

### Objectives

Mara Guard is designed to:

* Detect movement in monitored areas.
* Detect lions using the YOLOv8 artificial intelligence model.
* Provide a local deterrence response when a lion is detected.
* Transmit relevant detection and device information from field nodes.
* Provide rangers with timely monitoring and alert information.
* Support monitoring of device and power status.
* Maintain system information for monitoring and historical reference.
* Connect physical field devices with backend and user-facing applications.

### Success Metrics

The **North Star Metric** for Mara Guard is the number of **human-lion conflict incidents prevented**, measured through lion detection incidents identified by field nodes in the wild.

Mara Guard also uses activation and retention metrics to measure ranger engagement and continued use of the system.

| Metric                                 | Classification | Description                                                                                        | Collection Method                                                                   |
| -------------------------------------- | -------------- | --------------------------------------------------------------------------------------------------| ----------------------------------------------------------------------------------- |
| **Number of Detections Carried Out**   | North Star     | Total number of lions detected in the wild.                                                        | Recorded by the field node.        |
| **First Proactive Intervention**       | Activation     | First successful ranger response to a high-threat alert.                                                    | Recorded when a ranger acknowledges a live alert within the target response window. |
| **Daily Active Ranger Retention Rate** | Retention      | Percentage of trained rangers who continue monitoring alerts 30, 60, and 90 days after onboarding. | Measured using unique returning ranger user IDs over the relevant period.           |

These metrics help Mara Guard evaluate:

* **Detection effectiveness** — whether the system is identifying lion activity in monitored areas.
* **Ranger activation** — whether rangers receive and respond to important alerts.
* **Continued engagement** — whether rangers continue using the system after onboarding.

**Product Requirements Document (PRD):** [View the Mara Guard PRD](https://docs.google.com/document/d/1tuTnRjz8KZCSZ3Zoc_muYWbWJeVVfO5bCFa_Ot9bO7s/edit?tab=t.oofc6ghgswrm)

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## 7. Documentation Purpose and Maintenance

The technical documentation serves as the central source of technical knowledge for Mara Guard. It provides team members with the information needed to understand the system, set up the development environment, follow coding conventions, run tests, and understand how Mara Guard is deployed.

The documentation should remain aligned with the actual implementation. Changes to core functionality, architecture, setup procedures, coding standards, testing, or deployment should be reflected in the relevant documentation section before the associated Pull Request is considered complete.

The documentation serves both as an onboarding resource and as a maintained technical reference for Mara Guard.
