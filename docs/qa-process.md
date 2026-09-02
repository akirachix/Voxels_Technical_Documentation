# Quality Assurance & Testing Process

The Mara Guard QA protocol ensures that every deployed node operates reliably under extreme environmental conditions, maintains accurate edge inference, and guarantees fail-safe execution of automated deterrents.

---

## 1. QA Testing Framework Overview

The validation pipeline is broken into three distinct testing layers to isolate system issues completely prior to remote field deployment:

<div style="color: #bd936e; font-family: monospace; font-size: 16px; font-weight: bold; line-height: 1.8; white-space: pre; overflow: none; padding: 15px 0; text-align: center;">
[ HARDWARE UNIT ] &rarr; [ EDGE AI RIGOR ] &rarr; [ SYSTEM INTERNET ]
(Pinout/Current)        (YOLOv8 Matrix)       (MQTT/LoRa Loops)
</div>

---

## 2. Hardware Validation Protocols

### Electrical Safety & Isolation

* **Relay Kickback Verification:** Measure downstream voltage on the logic side during spotlight and acoustic horn toggle cycles. Confirm zero voltage leakage back to the Raspberry Pi 5 GPIO pins.
* **Current Draw Profiling:** Monitor telemetry outputs via the INA219 chip. Verify that maximum power consumption during simultaneous spotlight and siren activation does not exceed safe thermal boundaries or cause brownouts.

### Sensory Trigger Response

* **Radar Interrupt Testing:** Simulate physical motion boundaries up to 6 meters out. Verify that the microwave radar consistently pulls GPIO 17 high to successfully wake the camera module from low-power standby within 100 milliseconds.

---

## 3. Edge AI Model Accuracy Standards

### Inference Verification

* **False Positive Benchmarking:** Run benchmark datasets containing domestic livestock (cows, goats), guard dogs, and wind-blown brush through the localized YOLOv8 pipeline. The pipeline must match a classification threshold of zero false alarms before deployment.
* **True Positive Detection Target:** Ensure a confidence score of >= 90% on target lion profiles in low-light and infrared (IR) conditions before executing autonomous deterrent flags.

---

## 4. System-Wide Telemetry & Stress Testing

Our system-wide stability is validated through three distinct telemetry stress tests:

* **QA-LORA-01 (Transceiver Test):** We evaluate the LoRa Transceiver module by broadcasting 500 consecutive test data packets over our maximum intended physical field range. To pass this evaluation, the connection must remain stable with a packet loss rate strictly below 2%.

* **QA-MQTT-02 (Broker Test):** We evaluate the MQTT Broker by flooding the gateway network topics with a rapid stream of mock status JSON payloads. The system passes this test only if the ranger mobile app updates process and display the incoming data points within a strict sub-500-millisecond window.

* **QA-BATT-03 (Monitor Test):** We test our power diagnostics loop by artificially dropping the input battery voltage supply thresholds below 11 volts. The system passes if the INA219 monitoring chip successfully catches the drop and immediately transmits a low-power system warning packet back to the gateway base camp.


## 5. Environmental & Field Stress Testing

* **IP66 Ingress Verification:** Subject the fully assembled, weather-sealed chassis to sustained directional water jets and dust clouds. Inspect the internal electronics cabin for any moisture or fine particles.
* **Thermal Stress Profiles:** Run continuous YOLOv8 AI inference cycles inside a temperature-controlled environment matching extreme ambient heat peaks. Ensure the active cooling fan unit keeps the Raspberry Pi 5 core under 75°C.
