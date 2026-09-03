## 1. Executive Summary & Purpose
ឯកសារនេះរៀបរាប់អំពី **Software Process Architecture** សម្រាប់ការអភិវឌ្ឍប្រព័ន្ធ **Insulin Pump Control System** ដោយរួមបញ្ចូលគ្នារវាង **Spiral Model** និង **V-Model**។ 

គោលបំណងចម្បងគឺ៖
* ធានាបាននូវ **Safety-Critical Compliance** តាមស្តង់ដារវេជ្ជសាស្ត្រអន្តរជាតិ **IEC 62304 Class C**, **FDA Validation Guidelines**, និង **ISO 14971 (Risk Management)**។
* លុបបំបាត់ហានិភ័យ (Risks/Hazards) ទាំងអស់នៅដំណាក់កាលដំបូង។
* ផ្ទៀងផ្ទាត់ និងត្រួតពិនិត្យ (Verification & Validation) នូវរាល់តម្រូវការចាក់ថ្នាំ និងសុវត្ថិភាព ឱ្យមាន Bi-directional Traceability 100%។

---

## 2. Combined Process Model Architecture (Co-existence Model)

ការអភិវឌ្ឍត្រូវបែងចែកជា ២ ដំណាក់កាលធំៗជាលំដាប់លំដោយ ៖

```text
 [ ដំណាក់កាលទី ១: Risk-Driven Research ]       [ ដំណាក់កាលទី ២: Formal Engineering & Validation ]

          Spiral Model                                           V-Model
   - Concept & Objectives (URD)                           - Requirements Freeze (SRS)
   - Risk Analysis (ISO 14971)                            - System Architecture Design
   - Math Modeling & Prototyping                          - Detailed Module Design
   - Iterative Evaluation                                 - Implementation (Production Code)
                                                          - Verification & Validation (Testing)

                 |                                                         ^
                 |                                                         |
                 +---------> [ Requirements & Architecture Freeze ] -------+
```

---

## 3. Phase 1: Spiral Model Specification (Research & Risk Phase)

### 3.1 Overview & Scope
Spiral Model ត្រូវប្រើប្រាស់ **នៅដំណាក់កាលដំបូង មុនពេលសរសេរ Production Code** ដើម្បីធ្វើការសិក្សាស្រាវជ្រាវ (Research) និងវិភាគហានិភ័យ តាមរយៈការធ្វើ Iterative Cycles (រត់ជា Loop ៤ ជ្រុង)។

### 3.2 Detailed Execution in 4 Quadrants

| Quadrant | Name | Core Activities | Specific Insulin Pump Deliverables |
| :--- | :--- | :--- | :--- |
| **Q1** | **Determine Objectives** | កំណត់គោលដៅ លក្ខខណ្ឌកម្រិត (Constraints) តាម URD | កំណត់ Target Glucose Level, Daily Dose Limits ($D_{max}$), និង Sensor Sampling Frequency |
| **Q2** | **Risk Analysis & Prototyping** | ស្វែងរក Hazard តាម ISO 14971 និងបង្កើត Rapid Prototypes | **Hazard Analysis:** វិភាគករណី Sensor Noise, Overdose Risk, Signal Failure<br>**Prototyping:** បង្កើត Math Simulation (MATLAB/Python) តេស្ត Sensor Noise Filter (**SRS-FR-02**) |
| **Q3** | **Engineering & Evaluation** | តេស្ត Prototypes ជាមួយទិន្នន័យសប្បនិម្មិត (Simulated Data) | ផ្ទៀងផ្ទាត់ Dose Calculation Algorithm (**SRS-FR-04**) ជាមួយជាតិស្ករប្រែប្រួលខ្លាំង |
| **Q4** | **Plan Next Phase** | វាយតម្លៃលទ្ធផល៖ តើត្រូវរត់ Loop ទៀត ឬ Freeze Requirements? | **If Risks Exist:** ធ្វើផែនការចូល Loop បន្ទាប់<br>**If Clear:** Freeze URD/SRS ហើយផ្ទេរទៅ V-Model |

---

## 4. Phase 2: V-Model Specification (Formal Development & Testing Phase)

### 4.1 Overview & Scope
V-Model ត្រូវបានអនុវត្ត **នៅពេលដែល Requirements ត្រូវ freeze 100% ពី Spiral Model** ដើម្បីធ្វើការសរសេរ Production Code និងបង្កើតឯកសារសវនកម្ម (Audit Trail) តាម IEC 62304។

### 4.2 Mapping & Verification Workflow

```text
    [ Verification (Left Side) ]                                 [ Validation (Right Side) ]

  1. User Requirements (URD) -----------------------------> 8. User Acceptance Testing (UAT)
           \                                                       ^
            v                                                     /
  2. System Requirements (SRS) -------------------------> 7. System & Safety Testing
           \                                                       ^
            v                                                     /
  3. Architecture Design -------------------------------> 6. Integration Testing
           \                                                       ^
            v                                                     /
  4. Detailed Module Design ----------------------------> 5. Unit Testing
           \                                                       ^
            v                                                     /
             +---------------------------------------------------+
             |            Implementation & Code Freeze           |
             +---------------------------------------------------+
```

### 4.3 Phase-by-Phase Execution Details

* **1. User Requirements Document (URD):** កំណត់តម្រូវការអ្នកជំងឺ និងគ្រូពេទ្យ (ឧ. ការចាក់ថ្នាំស្វ័យប្រវត្តិ និងសុវត្ថិភាព)។
* **2. System Requirements Specification (SRS):** បំបែកជា **SRS-FR** (Functional: Dose Calculation, Sensor Filtering) និង **SRS-SR** (Safety: $D_{max}$ Clamp Safety Guardrail)។
* **3. Architecture Design:** ឌីសាញ Real-Time OS Scheduler, Inter-process Communication, និង Hardware Drivers Interfacing។
* **4. Detailed Module Design:** រៀបចំ Algorithm State Machines និង Floating-Point Math Conversion Formulas។
* **5. Unit Testing:** តេស្ត Function/Driver នីមួយៗ (ឧ. ផ្ទៀងផ្ទាត់ Dose Calc Function ដោយប្រៀបធៀប Mathematical Output)។
* **6. Integration Testing:** តេស្តការតភ្ជាប់រវាង Software Control Loop និង Hardware Motor Controller Subsystem។
* **7. System & Safety Testing:** ផ្ទៀងផ្ទាត់លក្ខខណ្ឌសុវត្ថិភាព និងល្បឿន Real-Time៖
  * **SRS-SR-01:** តេស្ត $D_{max}$ Clamp (ដាច់ខាតមិនឱ្យចាក់លើស)
  * **SRS-NFR-03:** ផ្ទៀងផ្ទាត់ Execution Time ឆ្លើយតប $\le 500	ext{ ms}$
* **8. User Acceptance Testing (UAT):** តេស្តលំហូរការងារទាំងមូលជាមួយ Clinical Simulator និងក្រុមគ្រូពេទ្យ។

---

## 5. Summary & Key Differences

| Aspect | Spiral Model (Phase 1) | V-Model (Phase 2) |
| :--- | :--- | :--- |
| **Primary Goal** | ស្វែងរក/លុបបំបាត់ Risk និងធ្វើ Prototype | សរសេរ Production Code និងធ្វើ Verification/Validation |
| **Execution Style** | Iterative Loops (៤ ជ្រុង) | Sequential & Traceable V-Shape |
| **Standards Focus** | **ISO 14971** (Risk Analysis) | **IEC 62304 / FDA** (Software Lifecycle) |
| **Requirements State** | ប្រែប្រួល និងអភិវឌ្ឍជាបន្តបន្ទាប់ (Refining URD/SRS) | ត្រូវ Freeze ១០០% មុននឹងចាប់ផ្តើម |