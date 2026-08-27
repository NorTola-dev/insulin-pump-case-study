## 1. Introduction

### 1.1 Purpose

This Software Requirements Specification (SRS) document details the complete functional, non-functional, interface, and safety requirements for the **Insulin Pump Control System software**. It translates high-level user requirements into precise, testable software specifications suitable for design, implementation, and safety validation.

### 1.2 Scope

The software operates within an embedded safety-critical medical device designed for continuous blood glucose monitoring and automated insulin delivery. The system boundary encompasses reading sensor data, calculating glucose levels and insulin doses, executing pulse-based pump actuation, triggering hardware alarms, and rendering user interface displays.

### 1.3 Definitions, Acronyms, and Abbreviations

- **URD:** User Requirements Document
- **SRS:** Software Requirements Specification
- **FR / NFR:** Functional Requirement / Non-Functional Requirement
- **SRS-FR / SRS-NFR:** Software Functional / Non-Functional Requirement Specification
- **Pulse:** A single discrete electrical command signal sent from the software controller to actuate one unit of insulin delivery.

### 1.4 Document Overview

This document covers detailed software requirements, system interfaces, process flow logic, safety constraints, hardware component interactions, and an explicit URD to SRS traceability matrix.

---

## 2. Overall Description

### 2.1 System Perspective

The Insulin Pump Control System software runs on an embedded micro-controller embedded within a closed-loop medical device environment. It directly interfaces with hardware peripherals:

- **Blood Sensor Input:** Periodic analog/digital data acquisition.
- **Insulin Pump Actuator Output:** Pulse generation output pins.
- **Clock Unit:** Real-time hardware interrupts for interval timing.
- **User Display & Alarm Interface:** Visual rendering and audible fault notifications.

### 2.2 System Functions

- Periodic acquisition and digital filtering of sensor readings.
- Blood glucose calculation and trend determination.
- Safety-bounded insulin dosage calculation.
- Pulse-based motor command generation.
- Real-time fault detection and alarm signaling.

### 2.3 User Characteristics

- **Primary User (Diabetic Patient):** Interacts with basic display outputs, system status indicators, and alarm alerts.
- **Secondary Users (Doctors, Nurses, Caregivers):** Inspect system status and historical delivery operational state.

### 2.4 Constraints

- The system is safety-critical; software errors could lead to severe medical harm.
- Hard real-time timing execution for sensor sampling and pump motor command generation.
- Memory and computational limits imposed by embedded hardware power constraints.

---

## 3. Specific Software Requirements

### 3.1 Software Functional Requirements (SRS-FR)

#### SRS-FR-01: Sensor Data Acquisition

- **Traceability:** URD FR-01
- **Khmer:** ផ្នែកទន់ត្រូវអានទិន្នន័យពី Blood Sensor តាមចន្លោះពេលកំណត់កំណត់ទុក (Periodic Interval)។
- **Specification:** The software shall acquire digital readings from the Blood Sensor interface at configured timing intervals ($T_{sample}$) via the hardware system clock.

#### SRS-FR-02: Sensor Data Validation and Analysis

- **Traceability:** URD FR-02
- **Khmer:** ផ្នែកទន់ត្រូវវិភាគ និងបញ្ជាក់ភាពត្រឹមត្រូវនៃទិន្នន័យ Sensor ដើម្បីស្វែងរក Out-of-bounds readings។
- **Specification:** The software shall filter raw sensor inputs, check for hardware measurement anomalies, and determine valid measurement ranges prior to calculation.

#### SRS-FR-03: Blood Glucose Calculation

- **Traceability:** URD FR-03
- **Khmer:** ផ្នែកទន់ត្រូវគណនាកម្រិតជាតិស្ករក្នុងឈាម (Blood Sugar Level) ចេញពីទិន្នន័យ Sensor វិភាគរួច។
- **Specification:** The software shall compute the current blood glucose concentration value based on calibrated conversion parameters from the validated sensor reading.

#### SRS-FR-04: Insulin Dose Calculation

- **Traceability:** URD FR-04
- **Khmer:** ផ្នែកទន់ត្រូវគណនាបរិមាណអាំងស៊ុយលីនដែលត្រូវចាក់ ដោយផ្អែកលើកម្រិតជាតិស្ករបច្ចុប្បន្ន។
- **Specification:** The software shall calculate the required insulin dosage based on the current computed blood glucose level and rate of change, constrained within preset minimum and maximum limits.

#### SRS-FR-05: Pump Command Sequence Generation

- **Traceability:** URD FR-05, FR-08
- **Khmer:** ផ្នែកទន់ត្រូវបម្លែងកម្រិតអាំងស៊ុយលីនដែលបានគណនា ទៅជាសញ្ញា Pulse សម្រាប់បញ្ជាទៅ Pump Motor។
- **Specification:** The software shall convert the calculated insulin dose into a discrete sequence of output control pulses, where exactly one pulse corresponds to one unit of insulin delivery.

#### SRS-FR-06: Pump Actuation Signal Control

- **Traceability:** URD FR-06, FR-07
- **Khmer:** ផ្នែកទន់ត្រូវបញ្ជូនសញ្ញា Pulse ទៅកាន់ Hardware Pump តាមលំដាប់លំដោយ និងពេលវេលាជាក់លាក់។
- **Specification:** The software shall drive the hardware Insulin Pump interface by transmitting the computed pulse sequence to actuate physical delivery.

#### SRS-FR-07: Continuous System Cycle & Monitoring

- **Traceability:** URD FR-09
- **Khmer:** ផ្នែកទន់ត្រូវដំណើរការ Loop តាមដានជាប្រចាំ ដោយមិនប៉ះពាល់ដល់ដំណើរការប្រព័ន្ធឡើយ។
- **Specification:** The software shall re-enter the data acquisition loop automatically after dose completion to maintain uninterrupted monitoring.

---

### 3.2 Non-Functional & Safety Requirements (SRS-NFR & SRS-SR)

#### SRS-NFR-01: High Availability

- **Traceability:** URD NFR-03, Key Req 1
- **Specification:** The software execution loop shall maintain an operational availability of 99.999%, ensuring continuous execution of sampling and command tasks.

#### SRS-NFR-02: Dose Accuracy & Calculation Reliability

- **Traceability:** URD NFR-02, NFR-04, Key Req 2
- **Specification:** Insulin dosage calculation functions shall execute with 0% tolerance for arithmetic overflow/underflow, adhering strictly to safe dosage formulas.

#### SRS-NFR-03: Real-Time Execution Constraints

- **Traceability:** URD NFR-05
- **Specification:** Sensor processing, dosage calculation, and command signal issuance shall complete within a maximum end-to-end execution budget ($T_{exec} \le 500\text{ ms}$) per cycle.

#### SRS-SR-01: Overdose Prevention Guard (Safety)

- **Traceability:** URD Safety Requirements
- **Specification:** The software shall enforce an absolute hard safety threshold ($D_{max}$) on single and cumulative daily insulin doses. Any calculation exceeding $D_{max}$ shall trigger a dose clamp and initiate an immediate safety alarm.

#### SRS-SR-02: Hardware Fault & Sensor Failure Alarm (Safety)

- **Traceability:** URD NFR-06, Safety Requirements
- **Specification:** If the sensor readings remain invalid or pump hardware handshake fails for two consecutive cycles, the software shall lock pump output in a safe state and trigger the Alarm interface.

---

## 4. Hardware Component Specifications

| Component        | Hardware Role                      | Software Interface Specification                                    |
| :--------------- | :--------------------------------- | :------------------------------------------------------------------ |
| **Blood Sensor** | Physical blood parameters          | Sampled via ADC/digital bus; software reads raw integer values.     |
| **Controller**   | Embedded MCU unit                  | Executes the compiled SRS core logic loop.                          |
| **Insulin Pump** | Physical mechanical pump           | Actuated by digital GPIO pulses ($1\text{ pulse} = 1\text{ unit}$). |
| **Clock**        | Hardware timer module              | Generates periodic timing interrupts for cyclic execution.          |
| **Alarm**        | Audible/visual hardware transducer | Triggered by software output pin in fault conditions.               |
| **Display**      | LCD/OLED output screen             | Software renders system status and glucose readings.                |

---

## 5. Software Process & Data Flow

### 5.1 System Flow Pipeline

```text
  +-------------------------------------------------------+
  |                     START CYCLE                       |
  +-------------------------------------------------------+
                              |
                              v
  +-------------------------------------------------------+
  | 1. SRS-FR-01: Read Sensor Input via Hardware Clock     |
  +-------------------------------------------------------+
                              |
                              v
  +-------------------------------------------------------+
  | 2. SRS-FR-02: Analyze & Validate Sensor Reading       |
  +-------------------------------------------------------+
                              |
             +----------------+----------------+
             |                                 |
 [Reading Valid]                       [Reading Invalid]
             |                                 |
             v                                 v
  +-----------------------+       +-----------------------+
  | 3. SRS-FR-03: Compute |       | SRS-SR-02: Trigger    |
  |    Blood Glucose      |       | Fault Alarm & Lockout |
  +-----------------------+       +-----------------------+
             |                                 |
             v                                 v
  +-----------------------+               [HALT CYCLE]
  | 4. SRS-FR-04: Compute |
  |    Insulin Dosage     |
  +-----------------------+
             |
             v
  +-------------------------------------------------------+
  | SRS-SR-01: Verify Safety Bounds (Dose <= D_max)       |
  +-------------------------------------------------------+
                              |
             +----------------+----------------+
             |                                 |
       [Within Limits]                   [Exceeds Limits]
             |                                 |
             v                                 v
  +-----------------------+       +-----------------------+
  | 5. SRS-FR-05: Generate|       | Clamp to D_max &      |
  |    Pump Pulses        |       | Trigger Safety Alarm  |
  +-----------------------+       +-----------------------+
             |                                 |
             v                                 v
  +-------------------------------------------------------+
  | 6. SRS-FR-06: Transmit Pulses to Actuate Pump         |
  +-------------------------------------------------------+
                              |
                              v
  +-------------------------------------------------------+
  | 7. SRS-FR-07: Log Data & Re-enter Monitoring Loop     |
  +-------------------------------------------------------+
```

---

## 6. URD to SRS Traceability Matrix

| URD ID     | URD Requirement Summary       | SRS Mapping ID | Software Realization Summary                                            |
| :--------- | :---------------------------- | :------------- | :---------------------------------------------------------------------- |
| **FR-01**  | Collect Sensor Information    | **SRS-FR-01**  | Reads periodic hardware sensor readings via clock interrupts.           |
| **FR-02**  | Analyze Sensor Reading        | **SRS-FR-02**  | Filters readings and verifies signal integrity.                         |
| **FR-03**  | Calculate Blood Sugar         | **SRS-FR-03**  | Converts raw values into blood glucose concentration.                   |
| **FR-04**  | Calculate Insulin Requirement | **SRS-FR-04**  | Computes dosage using target thresholds and rates of change.            |
| **FR-05**  | Generate Pump Commands        | **SRS-FR-05**  | Translates calculated dose into GPIO pulse trains.                      |
| **FR-06**  | Control Insulin Pump          | **SRS-FR-06**  | Outputs active electrical pulse signals to pump hardware.               |
| **FR-07**  | Deliver Insulin               | **SRS-FR-06**  | Actuates pump physical delivery via step-wise pulses.                   |
| **FR-08**  | Pulse-Based Delivery          | **SRS-FR-05**  | Enforces strict $1\text{ pulse} = 1\text{ unit}$ dose conversion logic. |
| **FR-09**  | Continuous Monitoring         | **SRS-FR-07**  | Continuously executes main software control loop.                       |
| **NFR-01** | Safety                        | **SRS-SR-01**  | Implements hard dosage ceiling clamps and lockouts.                     |
| **NFR-02** | Reliability                   | **SRS-NFR-02** | Ensures robust, fault-tolerant arithmetic routines.                     |
| **NFR-03** | Availability                  | **SRS-NFR-01** | Maintains 99.999% uptime execution.                                     |
| **NFR-04** | Accuracy                      | **SRS-NFR-02** | High-precision sensor calibration algorithms.                           |
| **NFR-05** | Response Time                 | **SRS-NFR-03** | Implements bounded cycle latency ($\le 500\text{ ms}$).                 |
| **NFR-06** | Fault Handling                | **SRS-SR-02**  | Hardware failure alarm routines and safe-state locks.                   |

---

## 7. Verification and Testing Direction

1. **Unit Testing:**
   - Test `Calculate_Blood_Sugar()` with boundary sensor values.
   - Verify arithmetic edge cases in `Compute_Insulin_Dose()`.

2. **Integration Testing:**
   - Verify clock interrupt triggers for data acquisition (`SRS-FR-01`).
   - Validate GPIO output pulse counts against requested dose integers (`SRS-FR-05`, `SRS-FR-06`).

3. **Safety & Hazard Testing (Fault Injection):**
   - Inject corrupted sensor signals to confirm immediate transition to `SRS-SR-02` alarm state.
   - Simulate software over-calculation to verify `SRS-SR-01` dosage clamp execution.

---

## 8. Summary Comparison: URD vs. SRS

- **URD Focus:** High-level operational needs from the patient/medical perspective (e.g., "The system shall calculate insulin requirement").
- **SRS Focus:** Low-level technical specifications for software developers (e.g., input data structures, calculation limits, signal timing constraints, safety clamps, and error handling routines).
