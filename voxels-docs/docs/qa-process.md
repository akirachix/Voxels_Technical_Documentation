# Quality Assurance & Testing Process

The Mara Guard QA protocol ensures that every deployed node operates reliably under extreme environmental conditions, maintains accurate edge inference, and guarantees fail-safe execution of automated deterrents.

---

## ## 1. QA Testing Framework Overview

The validation pipeline is broken into three testing layers to isolate issues before field deployment.

Use code with caution.[ HARDWARE UNIT TESTS ] -------> [ EDGE AI RIGOR TESTS ] -------> [ SYSTEM INTERNET STRESS ](Pinouts / Current Draw)         (YOLOv8 Confusion Matrix)       (MQTT / LoRa Telemetry Loops)
---

## ## 2. Hardware Validation Protocols

### ### Electrical Safety & Isolation
* **Relay Kickback Verification:** Measure downstream voltage on the logic side during spotlight and acoustic horn toggle cycles. Confirm zero voltage leakage back to the Raspberry Pi 5 GPIO pins.
* **Current Draw Profiling:** Monitor telemetry outputs via the **INA219 chip**. Verify that maximum power consumption during simultaneous spotlight and siren activation does not exceed safe thermal boundaries or cause brownouts.

### ### Sensory Trigger Response
* **Radar Interrupt Testing:** Simulate physical motion boundaries up to **6 meters** out. Verify that the microwave radar consistently pulls GPIO 17 high to successfully wake the camera module from low-power standby within 100 milliseconds.

---

## ## 3. Edge AI Model Accuracy Standards

### ### Inference Verification
* **False Positive Benchmarking:** Run benchmark datasets containing domestic livestock (cows, goats), guard dogs, and wind-blown brush through the localized **YOLOv8 pipeline**. The pipeline must match a classification threshold of **zero false alarms** before deployment.
* **True Positive Detection Target:** Ensure a confidence score of **>= 90%** on target lion profiles in low-light and infrared (IR) conditions before executing autonomous deterrent flags.

---

## ## 4. System-Wide Telemetry & Stress Testing

| Test ID | Target Component | Test Procedure | Expected Pass Criteria |
| :--- | :--- | :--- | :--- |
| **QA-LORA-01** | LoRa Transceiver | Broadcast 500 consecutive test packets over maximum physical range. | Packet loss rate must remain strictly below 2%. |
| **QA-MQTT-02** | MQTT Broker | Flood the gateway topic with rapid status JSON payloads. | Mobile app updates must process inside a <500ms window. |
| **QA-BATT-03** | INA219 Monitor | Artificially drop battery voltage supply thresholds below 11V. | System must successfully transmit a low-power warning packet. |

---

## ## 5. Environmental & Field Stress Testing

* **IP66 Ingress Verification:** Subject the fully assembled, weather-sealed chassis to sustained directional water jets and dust clouds. Inspect the internal electronics cabin for any moisture or fine particles.
* **Thermal Stress Profiles:** Run continuous YOLOv8 AI inference cycles inside a temperature-controlled environment matching extreme ambient heat peaks. Ensure the active cooling fan unit keeps the Raspberry Pi 5 core under 75°C.
