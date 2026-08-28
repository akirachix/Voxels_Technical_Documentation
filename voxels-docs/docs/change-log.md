# Change Log

All notable changes to the Mara Guard project will be documented in this file. This project adheres to Semantic Versioning.

---

## ## - 2026-08-28

### ### Added
* **QA Process Documentation:** Created `qa-process.md` establishing electrical safety checks, YOLOv8 true/false positive benchmarks, and environmental IP66 ingress stress tests.
* **Mobile Development Architecture:** Created `mobile-development.md` outlining the PWA/cross-platform application layout, MQTT JSON data payloads, and high-contrast night-mode UI requirements for field rangers.
* **Hardware Documentation:** Created `hardware-prototype.md` establishing the core physical specs for the **Raspberry Pi 5**, microwave radar sensor, relay isolation circuits, and the **INA219** telemetry module.
* **Data Flow Designs:** Integrated the **Voxels IoT Flow** logic system into structural sequential processing guides for edge-AI processing pipelines (YOLOv8 ingestion steps).

### ### Changed
* **System Component Definition:** Upgraded the system processor reference configuration from generic microcontroller boards to the high-performance **Raspberry Pi 5 Core** to natively support YOLOv8 local inferences.
* **Pin Mapping Schema:** Completed precise hardware assignment tables linking raw sensor outputs and point-to-point **LoRa modules** to target physical hardware headers on the central computing core.

---

## ## - 2026-08-20

### ### Added
* **Project Initialization:** Created core repository architecture including primary folders for documentation (`/docs`), styles, and asset structures.
* **High-Level Scope:** Initialized the foundational `how-it-works.md` file laying out the layered defense network concept inside the Maasai Mara National Reserve.
