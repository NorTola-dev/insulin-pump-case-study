# Functional Requirements Specification (FRS)
## Insulin Pump Control System

---

## 1. Overview
Document នេះផ្តោតលើ **Functional Requirements (តម្រូវការមុខងារ)** របស់ប្រព័ន្ធបញ្ជា Insulin Pump ដោយបញ្ជាក់ពីសកម្មភាព រូបមន្តគណនា និងលំហូរការងារដែលផ្នែកទន់ត្រូវអនុវត្ត។

---

## 2. Software Functional Requirements (SRS-FR)

### SRS-FR-01: Sensor Data Acquisition
* **Traceability:** URD FR-01
* **Khmer Description:** ផ្នែកទន់ត្រូវអានទិន្នន័យពី Blood Sensor តាមចន្លោះពេលកំណត់ទុក (Periodic Interval)។
* **Detailed Specification:** The software shall acquire digital readings from the Blood Sensor interface at configured timing intervals ($T_{sample}$) via the hardware system clock interrupt.

### SRS-FR-02: Sensor Data Validation and Analysis
* **Traceability:** URD FR-02
* **Khmer Description:** ផ្នែកទន់ត្រូវវិភាគ និងបញ្ជាក់ភាពត្រឹមត្រូវនៃទិន្នន័យ Sensor ដើម្បីស្វែងរក Out-of-bounds readings។
* **Detailed Specification:** The software shall filter raw sensor inputs, check for hardware measurement anomalies, and determine valid measurement ranges prior to calculation routines.

### SRS-FR-03: Blood Glucose Calculation
* **Traceability:** URD FR-03
* **Khmer Description:** ផ្នែកទន់ត្រូវគណនាកម្រិតជាតិស្ករក្នុងឈាម (Blood Sugar Level) ចេញពីទិន្នន័យ Sensor វិភាគរួច។
* **Detailed Specification:** The software shall compute the current blood glucose concentration value based on calibrated conversion parameters from the validated sensor reading.

### SRS-FR-04: Insulin Dose Calculation
* **Traceability:** URD FR-04
* **Khmer Description:** ផ្នែកទន់ត្រូវគណនាបរិមាណអាំងស៊ុយលីនដែលត្រូវចាក់ ដោយផ្អែកលើកម្រិតជាតិស្ករបច្ចុប្បន្ន។
* **Detailed Specification:** The software shall calculate the required insulin dosage based on the current computed blood glucose level and rate of change, constrained within preset minimum and maximum parameters.

### SRS-FR-05: Pump Command Sequence Generation
* **Traceability:** URD FR-05, FR-08
* **Khmer Description:** ផ្នែកទន់ត្រូវបម្លែងកម្រិតអាំងស៊ុយលីនដែលបានគណនា ទៅជាសញ្ញា Pulse សម្រាប់បញ្ជាទៅ Pump Motor។
* **Detailed Specification:** The software shall convert the calculated insulin dose into a discrete sequence of output control pulses, where exactly one pulse corresponds to one unit of insulin delivery ($1\text{ pulse} = 1\text{ unit}$).

### SRS-FR-06: Pump Actuation Signal Control
* **Traceability:** URD FR-06, FR-07
* **Khmer Description:** ផ្នែកទន់ត្រូវបញ្ជូនសញ្ញា Pulse ទៅកាន់ Hardware Pump តាមលំដាប់លំដោយ និងពេលវេលាជាក់លាក់។
* **Detailed Specification:** The software shall drive the hardware Insulin Pump interface by transmitting the computed pulse sequence via designated GPIO pins to actuate physical delivery.

### SRS-FR-07: Continuous System Cycle & Monitoring
* **Traceability:** URD FR-09
* **Khmer Description:** ផ្នែកទន់ត្រូវដំណើរការ Loop តាមដានជាប្រចាំ ដោយមិនប៉ះពាល់ដល់ដំណើរការប្រព័ន្ធឡើយ។
* **Detailed Specification:** The software shall re-enter the data acquisition loop automatically after dose completion to maintain uninterrupted monitoring.

---

## 3. Functional Traceability Matrix

| URD ID | Functional Requirement Summary | SRS Mapping ID | Software Realization Summary |
| :--- | :--- | :--- | :--- |
| **FR-01** | Collect Sensor Information | **SRS-FR-01** | Reads periodic hardware sensor readings via clock interrupts. |
| **FR-02** | Analyze Sensor Reading | **SRS-FR-02** | Filters readings and verifies signal integrity. |
| **FR-03** | Calculate Blood Sugar | **SRS-FR-03** | Converts raw values into blood glucose concentration. |
| **FR-04** | Calculate Insulin Requirement | **SRS-FR-04** | Computes dosage using target thresholds and rates of change. |
| **FR-05** | Generate Pump Commands | **SRS-FR-05** | Translates calculated dose into GPIO pulse trains. |
| **FR-06** | Control Insulin Pump | **SRS-FR-06** | Outputs active electrical pulse signals to pump hardware. |
| **FR-07** | Deliver Insulin | **SRS-FR-06** | Actuates pump physical delivery via step-wise pulses. |
| **FR-08** | Pulse-Based Delivery | **SRS-FR-05** | Enforces strict $1\text{ pulse} = 1\text{ unit}$ dose conversion logic. |
| **FR-09** | Continuous Monitoring | **SRS-FR-07** | Continuously executes main software control loop. |

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
