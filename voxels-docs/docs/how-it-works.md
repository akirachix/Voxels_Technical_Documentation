

Mara Guard is an automated, edge-AI-powered wildlife conflict mitigation system designed to protect livestock and prevent retaliatory lion killings in the Maasai Mara National Reserve. 

The entire system operates as a **layered defense network**, combining localized sensing, edge intelligence, autonomous deterrents, and long-range telemetry to intercept threats before conflict occurs.

---

## 1. The Core Functional Workflow

The end-to-end processing pipeline runs autonomously on-site across four explicit operational phases:


[1. RADAR TRIGGER] ──> [2. EDGE AI PROCESSING] ──> [3. LOCAL DETERRENT] ──> [4. LORA/MQTT TELEMETRY]
Motion within 6m       Raspberry Pi 5 + YOLOv8      Spotlight + Siren Fired     Ranger Dashboard Updated


### Phase 1: All-Weather Perimeter Ingestion
* **Sensing Threshold:** An industrial microwave radar sensor monitors a perimeter boundary zone up to **6 meters** from the field node.
* **Environmental Resilience:** Unlike passive infrared sensors, the radar tracking unit functions reliably in dense fog, heavy rain, dust storms, and extreme midnight heat.
* **Camera Awakening:** The moment physical motion breaks the radar tracking field, a hardware interrupt awakens the localized video capture camera to stream live field frames.

### Phase 2: Local Edge AI Analysis
* **On-Board Computation:** Frame packets are sent straight to a localized **Raspberry Pi 5** computer running inside the weather-sealed chassis. 
* **Model Inference:** The node runs a highly optimized **YOLOv8 computer vision model** directly on the edge, eliminating any reliance on stable cloud computation or active internet streams.
* **Target Classification:** The local framework parses frames looking for matches matching class: lion. If the pipeline detects a domestic guard dog, herder, livestock animal, or blowing brush, the signal is dropped instantly to achieve **zero false alarms**.

### Phase 3: Layered Autonomous Deterrence
If a high-confidence lion profile match is confirmed, the device fires an immediate, escalating sequence of physical deterrent flags:
* **Visual Shock:** The control unit switches on a high-lumen structural spotlight to disorient and startle the nocturnal hunting vision of the animal.
* **Acoustic Blast:** Simultaneously, an onboard acoustic horn blasts an intense siren loop to create an immediate fight-or-flight acoustic barrier.
* **Multi-Threat Scale:** If the tracking module registers a multi-lion pride profile, the hardware keeps the sirens and spotlights firing continuously until the count drops to zero and all lions exit the boundary area.

### Phase 4: Long-Range Telemetry Link
* **Radio Broadcast:** Once a deterrent cycle initiates, the system logs the incident data (timestamp, count, node ID, and battery health tracked via an **INA219 monitoring chip**).
* **Network Failover:** The node broadcasts a compact packet using point-to-point **LoRa radio frequency loops**. This telemetry travels directly to a base gateway over long distances without requiring cellular towers.
* **Dashboard Push:** The gateway consumes the radio signal and maps it over an **MQTT broker connection**, instantly populating the active intrusion dashboard viewed by rangers in the field hub.

---

## 2. Technical System Specifications
<div class="custom-card-container">
  <div class="custom-card" style="flex: 1 1 100% !important; background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">System Component Matrix</h3>
    <p style="color: #42281A !important;">Structural breakdown and operational profiles of the deployed field hardware nodes:</p>
    <table style="width: 100%; border-collapse: collapse; margin-top: 12px;">
      <thead>
        <tr style="border-bottom: 2px solid #CD8151; text-align: left;">
          <th style="color: #2D1A10 !important; padding: 8px;">Structural Layer</th>
          <th style="color: #2D1A10 !important; padding: 8px;">Component Used</th>
          <th style="color: #2D1A10 !important; padding: 8px;">Operational Threshold</th>
        </tr>
      </thead>
      <tbody>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #42281A !important; padding: 8px;"><strong>Power Supply</strong></td>
          <td style="color: #42281A !important; padding: 8px;">Photovoltaic Solar Array</td>
          <td style="color: #42281A !important; padding: 8px;">24/7 autonomous battery cycle</td>
        </tr>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #42281A !important; padding: 8px;"><strong>Telemetry Node</strong></td>
          <td style="color: #42281A !important; padding: 8px;">Point-to-Point LoRa Transceiver</td>
          <td style="color: #42281A !important; padding: 8px;">Direct radio packet broadcasting</td>
        </tr>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #42281A !important; padding: 8px;"><strong>Power Tracking</strong></td>
          <td style="color: #42281A !important; padding: 8px;">INA219 Sensor Module</td>
          <td style="color: #42281A !important; padding: 8px;">Real-time voltage & battery health parsing</td>
        </tr>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #42281A !important; padding: 8px;"><strong>Local Host</strong></td>
          <td style="color: #42281A !important; padding: 8px;">Raspberry Pi 5</td>
          <td style="color: #42281A !important; padding: 8px;">Localized script and model execution</td>
        </tr>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #42281A !important; padding: 8px;"><strong>AI Classifier</strong></td>
          <td style="color: #42281A !important; padding: 8px;">Custom YOLOv8 Model Framework</td>
          <td style="color: #42281A !important; padding: 8px;">Multi-object classification & density tracking</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>


---

## 3. Operational Outcomes for Field Staff

By handling threat validation directly on the edge hardware, Mara Guard solves critical pain points for field rangers like **Sanaiyan Nanyoike**:
* **Proactive Security:** Instead of managing community anger after a livestock attack, rangers receive actionable notifications minutes before a conflict occurs.
* **True Threat Filtering:** The web monitoring dashboard updates *only* when real lions are validated. Rangers avoid waking up or rushing out into danger to check false radar triggers caused by weather elements.
* **System Health Visibility:** Every data push carries battery level updates from the INA219 sensor, ensuring field technicians can replace or maintain solar hardware nodes before they fail in the field.
