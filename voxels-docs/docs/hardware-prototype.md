# Hardware Prototype Architecture

The Mara Guard hardware node is built for rugged, remote deployment in the Maasai Mara National Reserve. It balances power-efficient standby modes with high-performance edge AI computation, sensory ingestion, and long-range communication.

---

## ## 1. System Block Diagram & Interfaces

The entire platform operates on an edge-hub topology, connecting low-power sensors and high-draw deterrents directly to a centralized, weather-sealed computing core.

[ RADAR TRIGGER ] --------(GPIO Interrupt)-------> [ RASPBERRY PI 5 ] <-------(I2C Bus)-------> [ INA219 CHIP ]|+-------------------+-------------------+| (MIPI CSI Port)   | (GPIO Relay)      | (SPI Bus)v                   v                   v[ CAMERA MODULE ]   [ DETERRENT CORES ] [ LoRa RADIO MODULE ](Spotlight/Horn)
---

## ## 2. Core Hardware Specifications

### ### Physical & Computational Core
* **Main Processor:** **Raspberry Pi 5** (8GB RAM configuration) running a lightweight, headless Linux environment optimized for edge AI inference.
* **Thermal Regulation:** Active cooling fan with aluminum heatsinks housed within an IP66-rated, dustproof, and weather-sealed enclosure.

### ### Sensory Ingestion Subsystem
* **Radar Module:** Industrial microwave radar sensor operating on a continuous detection loop.
* **Camera Module:** High-definition, low-light infrared (IR) camera module connected via the onboard MIPI CSI interface.

### ###  Deterrent Subsystem
* **Visual Deterrent:** High-lumen structural spotlight connected through an optically isolated **5V/12V dual-channel relay board** to protect logic pins.
* **Acoustic Deterrent:** High-decibel onboard acoustic horn blast siren triggered via dedicated GPIO switching logic.

### ### Power & Telemetry Monitoring
* **Telemetry Sensor:** **INA219 High-Side Current and Voltage Monitor** communicating via the hardware **I2C bus**.
* **Power Source:** Heavy-duty external battery pack built to withstand high extreme ambient heat fluctuations.

### ### Long-Range Transceiver
* **Communication Chip:** Point-to-point **LoRa radio module** interfaced via the hardware **SPI bus** for low-power, cell-tower-free telemetry transmission.

---

## ## 3. Hardware Logic Flow (Sequential Processing)

1. **All-Weather Ingestion Loop:** The industrial microwave radar sensor monitors the 6-meter boundary line. The camera sits in a low-power sleep state.
2. **Hardware Interrupt Trigger:** When physical motion breaks the radar tracking zone, a hardware interrupt signal forces the camera to instantly awaken.
3. **Edge Video Streaming:** The camera streams live, low-light video frames directly over the MIPI CSI channel straight into the Raspberry Pi 5 memory space.
4. **Local YOLOv8 Inference:** The localized computer running inside the chassis processes the frame frames via a native **YOLOv8 target classification model**. If a lion profile matches, the pipeline proceeds; if domestic stock or an accidental brush movement is caught, the frame drops.
5. **Layered Deterrent Flags:** Upon target confirmation, the Pi pulls designated relay GPIO lines high, triggering a dual blast of the high-lumen structural spotlight and the acoustic siren horn loop.
6. **Telemetry Packaging:** The **INA219 tracking module** captures voltage, current draw, and total remaining capacity. This diagnostic log is aggregated alongside the incident timestamps.
7. **Point-to-Point Uplink:** The telemetry footprint broadcasts wirelessly over point-to-point **LoRa frequencies** back to a local base station gateway, routing straight out to the rangers' field dashboard.

---

## ## 4. Detailed Hardware Pinout Mapping

| Component Module | Hardware Pin Name | Raspberry Pi 5 Pin / Interface | Purpose / Description |
| :--- | :--- | :--- | :--- |
| **Microwave Radar** | OUT (Digital) | GPIO 17 (Pin 11) | Hardware interrupt to wake camera from standby |
| **Camera Module** | Flex Ribbon Cable | MIPI CSI Port 0 | High-speed video frame streaming |
| **Relay 1 (Spotlight)**| IN1 (Active Low) | GPIO 27 (Pin 13) | Controls power line switching for the structural spotlight |
| **Relay 2 (Siren Horn)**| IN2 (Active Low) | GPIO 22 (Pin 15) | Controls power line switching for the acoustic horn |
| **INA219 Monitor** | SDA / SCL | GPIO 2 / GPIO 3 (I2C) | Real-time voltage, current, and battery health tracking |
| **LoRa Module** | MOSI/MISO/SCK/CS | SPI0 Bus (Pins 19, 21, 23, 24) | Point-to-point long-range radio data loops |

---

## ## 5. Assembly & Prototyping Protocols

### ### Phase 1: Power Isolation & Safety
* **Optocoupled Isolation:** Never connect high-current power lines from the spotlight or acoustic siren directly to the Raspberry Pi GPIO headers. Always route them through the isolated relay board channel interfaces.
* **Ground Sharing:** Ensure a common ground (`GND`) loop is established exclusively between the logic side of the sensors, the INA219 tracking module, and the Raspberry Pi ground pins to prevent floating signal data.

### ### Phase 2: Weatherproofing & Heat Management
* **Enclosure Sealing:** Pass all external wiring (Radar out lines, Camera flex ribbons, Power lines to Spotlight) through protective rubber cable glands to maintain the IP66 ingress protection rating against heavy dust storms and rain.
* **Heatsink Fitting:** Apply thermal paste or high-conductivity thermal pads between the Raspberry Pi 5 SoC and the active cooling fan chassis before sealing the node closed.