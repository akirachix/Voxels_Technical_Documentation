# System Architecture Blueprint

Mara Guard is a smart, solar-powered security network built for the field. It uses edge AI to process camera and sensor data right on the spot, triggering immediate alarms while pushing live tracking updates straight to the rangers' dashboard.
---

## ## 1. End-to-End System Architecture Map

The system maps out across five core execution stages, tracking everything from raw solar power harvesting up to database record cold-storage:

[ Solar Panel ] ---> [ Power Module ] ---(Battery Level)---> [ INA219 ] ---> [ Raspberry Pi 5 Core ]^[ Camera Module ] ---------(Live Video Frame Stream)-------------------------------+[ Ultrasonic Sensor ] -----(Proximity Distance Matrix)-------------------------------+|v[ Automated Deterrents ] <---(Spotlight / Siren Audio Blast)-----------------------+|v (LoRa Data Packet)[ Paylink Gateway / Router ]|v (MQTT Protocol)[ Central MQTT Broker ]|v (Data Sync Pipeline)[ Trained Model Core ] <=========> [ Train Analysis Module ] <=========> [ Ranger Mobile PWA ]|v (API Call Integration)[ Core Service API Gears ]|v (Data Persistence)[ Relational Database ]
---

## ## 2. Detailed Technical Block Breakdown

### ### Power Generation & Diagnostic Management
* **Solar Panel Matrix:** Charges the central battery bank in remote field areas to maintain autonomous, off-grid network lifespan.
* **Power Module:** Conditions input lines and scales voltage thresholds safely for system-side delivery.
* **INA219 Chip Sensor:** Sample high-side voltage and current values directly from the Power Module, feeding live battery health analytics over the I2C bus into the primary processor core.

### ### Local Ingestion, Inference & Deterrence (The Field Node)
* **Multimodal Edge Sensing:** Ingests synchronized environmental streams via a high-definition **Camera Module** (live video) and an **Ultrasonic Proximity Sensor** (target space parameters).
* **Raspberry Pi 5 Compute Engine:** Runs local target tracking and edge computation loops. Raw frames are passed natively through a localized **YOLOv8 target detection pipeline**.
* **Isolated Actuators / Deterrents:** If the classification engine flags a verified threat, the Pi pulls designated relay pins high to trigger physical counter-measures instantly, firing the **high-intensity spotlight** and the **acoustic alert horn** simultaneously.

### ### Backhaul, Brokerage & Processing Tier
* **Paylink Gateway / Router:** Collects point-to-point data packets containing location telemetry, incident metrics, and power health indices from the edge node.
* **MQTT Broker Core:** Translates raw ingestion signals into standardized JSON payloads, routing tracking lines through explicit pub/sub communication topics.
* **Train Analysis Module:** Manages active system workflows. It interacts with the **Trained Model Core** container to optimize tracking weights and feeds real-time status arrays down to the **Ranger Mobile PWA Dashboard**.

### ### Core API & Long-Term Data Persistence
* **Service API Gears:** Exposes secure REST endpoints to handle dashboard authentication, historical analysis lookups, and administrative tracking profiles.
* **Relational Database Storage:** Acts as the final system storage layer, indexing localized incident tracking data, node diagnostic telemetry, and chronological ranger response logs.

---

## ## 3. Communication Protocols & Data Contracts

Data transmissions strictly map across explicitly defined messaging standard formats:

| Core System Interface | Interfacing Protocol | Data Serialization / Style |
| :--- | :--- | :--- |
| **Field Node -> Paylink Gateway** | Point-to-Point LoRa Radio | Compact Binary Packets |
| **Paylink Gateway -> MQTT Broker**| MQTT Protocol | JSON Message Strings |
| **Train Module -> Ranger Mobile PWA** | WebSockets Over TLS | Event-Driven JSON Payloads |
| **Application Layer Component Links**| RESTful HTTPS APIs | Clean JSON Schemas |

---

## ## 4. System Isolation & Fail-Safe Protocols

* **Power Safety Margins:** The INA219 power tracker checks that high-inductive actuator draws (spotlight/horn) do not cross dangerous limits, preventing field crashes due to battery exhaustion.
* **Offline Routing Fallbacks:** If the gateway internet uplink drops out entirely, the Train Analysis Module queues incoming data packets internally to ensure data stays preserved until the system reconnects.
