# Non-Functional & Safety Requirements Specification (NFRS)
## Insulin Pump Control System

---

## 1. Overview
Document នេះផ្តោតលើ **Non-Functional Requirements (តម្រូវការក្រៅពីមុខងារ)** និង **Safety Requirements (តម្រូវការសុវត្ថិភាព)** របស់ប្រព័ន្ធបញ្ជា Insulin Pump ដោយកំណត់ស្តង់ដារគុណភាព ល្បឿន ភាពជឿជាក់ និងកម្រិតការពារគ្រោះថ្នាក់។

---

## 2. Software Non-Functional Requirements (SRS-NFR)

### SRS-NFR-01: High Availability
* **Traceability:** URD NFR-03, Key Req 1
* **Khmer Description:** ប្រព័ន្ធត្រូវដំណើរការរលូនដោយគ្មានការរអាក់រអួល រហូតដល់ 99.999%។
* **Detailed Specification:** The software execution loop shall maintain an operational availability of 99.999%, ensuring continuous execution of sampling and command tasks without unscheduled down-time.

### SRS-NFR-02: Dose Accuracy & Calculation Reliability
* **Traceability:** URD NFR-02, NFR-04, Key Req 2
* **Khmer Description:** ការគណនាត្រូវមានភាពត្រឹមត្រូវ 100% ដោយមិនឱ្យមានកំហុស Arithmetic Overflow/Underflow ឡើយ។
* **Detailed Specification:** Insulin dosage calculation functions shall execute with 0% tolerance for arithmetic overflow/underflow, adhering strictly to safe dosage formulas and high-precision calibration.

### SRS-NFR-03: Real-Time Execution Constraints
* **Traceability:** URD NFR-05
* **Khmer Description:** ល្បឿនរង្វង់ប្រតិបត្តិការ (End-to-End Cycle) ត្រូវបញ្ចប់ក្នុងរយៈពេលយ៉ាងយូរបំផុត 500ms។
* **Detailed Specification:** Sensor processing, dosage calculation, and command signal issuance shall complete within a maximum end-to-end execution budget ($T_{exec} \le 500\text{ ms}$) per monitoring cycle.

---

## 3. Software Safety Requirements (SRS-SR)

### SRS-SR-01: Overdose Prevention Guard (Safety)
* **Traceability:** URD Safety Requirements
* **Khmer Description:** កម្រិតសុវត្ថិភាពខ្ពស់បំផុត ($D_{max}$) — បើការគណនាលើសកំណត់ ផ្នែកទន់ត្រូវ Clamp បរិមាណថ្នាំ ហើយបញ្ជូន Alarm សុវត្ថិភាពភ្លាមៗ។
* **Detailed Specification:** The software shall enforce an absolute hard safety threshold ($D_{max}$) on single and cumulative daily insulin doses. Any calculation exceeding $D_{max}$ shall trigger a dose clamp and initiate an immediate safety alarm.

### SRS-SR-02: Hardware Fault & Sensor Failure Alarm (Safety)
* **Traceability:** URD NFR-06, Safety Requirements
* **Khmer Description:** បើ Sensor ឬ Pump មានបញ្ហា 2 cycles ជាប់គ្នា ផ្នែកទន់ត្រូវ Lockout ប្រព័ន្ធ និងបន្លឺ Alarm អាសន្ន។
* **Detailed Specification:** If the sensor readings remain invalid or pump hardware handshake fails for two consecutive cycles, the software shall lock pump output in a safe state and trigger the hardware Alarm interface.

---

## 4. Non-Functional & Safety Traceability Matrix

| URD ID | Non-Functional Requirement Summary | SRS Mapping ID | Software Realization Summary |
| :--- | :--- | :--- | :--- |
| **NFR-01** | Safety | **SRS-SR-01** | Implements hard dosage ceiling clamps and lockouts. |
| **NFR-02** | Reliability | **SRS-NFR-02** | Ensures robust, fault-tolerant arithmetic routines. |
| **NFR-03** | Availability | **SRS-NFR-01** | Maintains 99.999% uptime execution. |
| **NFR-04** | Accuracy | **SRS-NFR-02** | High-precision sensor calibration algorithms. |
| **NFR-05** | Response Time | **SRS-NFR-03** | Implements bounded cycle latency ($T_{exec} \le 500\text{ ms}$). |
| **NFR-06** | Fault Handling | **SRS-SR-02** | Hardware failure alarm routines and safe-state locks. |

## 4. Requirement Relationships & Traceability Dependencies

### 4.1 Structural Relationship Analysis
Functional Requirements មិនអាចដំណើរការដាច់ដោយឡែកដោយគ្មានការតភ្ជាប់ជាមួយ Non-Functional & Safety Requirements នោះទេ៖

* **Dose Accuracy & Calculation Safeguard (SRS-FR-04 $\leftrightarrow$ SRS-NFR-02):** 
  * មុខងារគណនាថ្នាំក្នុង **SRS-FR-04** ត្រូវបានត្រួតពិនិត្យដោយស្តង់ដារ **SRS-NFR-02** ដើម្បីធានាថាគ្មាន Precision Error ក្នុងការបម្លែងទិន្នន័យឡើយ។
* **Real-Time Execution Pipeline (SRS-FR-01 $\to$ SRS-FR-06 $\leftrightarrow$ SRS-NFR-03):** 
  * លំហូរប្រតិបត្តិការពីការអាន Sensor រហូតដល់ការបញ្ជូន Pulse (FR-01 ដល់ FR-06) ត្រូវតែបញ្ចប់ក្នុងរង្វង់ពេលរត់ $T_{exec} \le 500\text{ ms}$ តាម **SRS-NFR-03**។
* **Overdose Prevention Guard (SRS-FR-05 / SRS-FR-06 $\leftrightarrow$ SRS-SR-01):** 
  * មុនពេលបម្លែង Pulse បញ្ជូនទៅ Hardware Pump (**SRS-FR-05 & SRS-FR-06**) ប្រព័ន្ធត្រូវឆ្លងកាត់ Safety Hard Ceiling Clamp ($D_{max}$) នៃ **SRS-SR-01** ជាមុនសិន។

### 4.2 Cross-Requirement Interaction Matrix

| Functional Requirement (FR) | Associated NFR / SR | Nature of Relationship | Operational Constraint |
| :--- | :--- | :--- | :--- |
| **SRS-FR-01:** Sensor Acquisition | **SRS-NFR-01:** High Availability | Execution Constraint | ការអានទិន្នន័យធ្វើឡើងបន្តបន្ទាប់ដោយគ្មានការរអាក់រអួល (99.999% Availability)។ |
| **SRS-FR-02:** Sensor Validation | **SRS-SR-02:** Hardware Fault Handling | Safety Fallback | បើទិន្នន័យមិនប្រក្រតី 2 cycles ជាប់គ្នា នោះប្រព័ន្ធនឹងផ្លាស់ប្តូរទៅ SR-02 ដើម្បី Lockout Pump និងបន្លឺ Alarm។ |
| **SRS-FR-03:** Glucose Calculation | **SRS-NFR-02:** Calculation Reliability | Accuracy Guard | បង្ការ Floating Point Overflow/Underflow ពេលគណនាកម្រិតជាតិស្ករ។ |
| **SRS-FR-04:** Insulin Dose Calculation | **SRS-SR-01:** Overdose Prevention | Safety Bound | កម្រិតចំនួនថ្នាំអតិបរមា ($D_{max}$) មិនឱ្យលើសពីកម្រិតសុវត្ថិភាព មិនថាស្ថិតក្នុងស្ថានភាពបែបណាឡើយ។ |
| **SRS-FR-05 & SRS-FR-06:** Pump Control | **SRS-NFR-03:** Real-Time Execution | Latency Limit | បញ្ជូន Pulse ទៅ Hardware ទាន់ពេលវេលាជាក់ស្តែង ($\le 500\text{ ms}$)។ |
| **SRS-FR-07:** Continuous Loop | **SRS-NFR-01:** System Uptime | Operational Stability | រក្សា Loop ដំណើរការជាប្រចាំដោយគ្មាន Crash ឬ Freeze។ |