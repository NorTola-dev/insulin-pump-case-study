# Insulin Pump Control System

## 1. Project Overview

The **Insulin Pump Control System** is an embedded medical system designed to help people with diabetes by monitoring blood sugar levels and controlling an insulin pump.

The system receives information from a blood sensor, calculates the patient's blood sugar level and the amount of insulin required, and then sends control signals to an insulin pump.

The insulin pump delivers insulin through a permanently attached needle. The system is considered **safety-critical** because an incorrect insulin dose can cause serious health problems.

This case study is based on the insulin pump case study described in **Ian Sommerville's Software Engineering**.

---

# 2. Objectives

The main objectives of the system are:

1. Monitor the patient's blood sugar level.
2. Analyze information received from the blood sensor.
3. Calculate the amount of insulin required.
4. Control the insulin pump.
5. Deliver the correct amount of insulin.
6. Continue monitoring the patient's blood sugar level.
7. Operate reliably and safely.

The original case study identifies two essential high-level requirements:

* The system shall be available to deliver insulin when required.
* The system shall perform reliably and deliver the correct amount of insulin to counteract the current blood sugar level.

---

# 3. System Users / Stakeholders

## Primary User

* **Diabetic Patient** — The person who uses the insulin pump.

## Other Stakeholders

* Doctor
* Nurse
* Caregiver

The published case-study materials identify the diabetic patient as the main user and doctors, caregivers, and nurses as indirect users.

---

# 4. System Components

The main components of the insulin pump system are:

| Component         | Description                                                            |
| ----------------- | ---------------------------------------------------------------------- |
| Blood Sensor      | Measures a blood parameter related to the patient's blood sugar level. |
| Controller        | Processes sensor information and calculates the required insulin dose. |
| Insulin Pump      | Delivers insulin according to commands from the controller.            |
| Insulin Reservoir | Stores insulin for delivery.                                           |
| Needle Assembly   | Delivers insulin into the patient's body.                              |
| Clock             | Provides timing information to the controller.                         |
| Alarm             | Provides an alarm when an error or abnormal condition occurs.          |
| Display           | Provides information to the user.                                      |
| Power Supply      | Provides power to the system.                                          |

The published architecture of the case study includes the sensor, controller, pump, clock, alarm, displays, insulin reservoir, needle assembly, and power supply.

---

# 5. User Requirements Document (URD)

## 5.1 Purpose

The purpose of the URD is to describe what the insulin pump system must provide for its users and stakeholders.

---

## 5.2 Functional Requirements

Functional requirements describe **what the system must do**.

### FR-01 — Collect Sensor Information

**English:**
The system shall collect information from the blood sensor.

**Khmer:**
ប្រព័ន្ធត្រូវទទួលព័ត៌មានពីឧបករណ៍ Blood Sensor។

---

### FR-02 — Analyze Sensor Reading

**English:**
The system shall analyze the information received from the blood sensor.

**Khmer:**
ប្រព័ន្ធត្រូវវិភាគព័ត៌មានដែលទទួលបានពី Blood Sensor។

---

### FR-03 — Calculate Blood Sugar

**English:**
The controller shall calculate the patient's blood sugar level from the sensor information.

**Khmer:**
Controller ត្រូវគណនាកម្រិតជាតិស្ករក្នុងឈាមរបស់អ្នកជំងឺពីព័ត៌មានរបស់ Sensor។

---

### FR-04 — Calculate Insulin Requirement

**English:**
The system shall calculate the amount of insulin required based on the blood sugar information.

**Khmer:**
ប្រព័ន្ធត្រូវគណនាបរិមាណអាំងស៊ុយលីនដែលត្រូវការ ដោយផ្អែកលើព័ត៌មានកម្រិតជាតិស្ករក្នុងឈាម។

---

### FR-05 — Generate Pump Commands

**English:**
The controller shall generate commands for controlling the insulin pump.

**Khmer:**
Controller ត្រូវបង្កើតពាក្យបញ្ជាសម្រាប់គ្រប់គ្រង Insulin Pump។

---

### FR-06 — Control Insulin Pump

**English:**
The controller shall send signals to the insulin pump.

**Khmer:**
Controller ត្រូវបញ្ជូនសញ្ញាទៅ Insulin Pump។

---

### FR-07 — Deliver Insulin

**English:**
The insulin pump shall deliver the required amount of insulin.

**Khmer:**
Insulin Pump ត្រូវបញ្ចេញអាំងស៊ុយលីនតាមបរិមាណដែលត្រូវការ។

---

### FR-08 — Pulse-Based Delivery

**English:**
The pump shall deliver one unit of insulin for each pulse received from the controller.

**Khmer:**
Pump ត្រូវបញ្ចេញអាំងស៊ុយលីនមួយ Unit សម្រាប់ Pulse មួយដែលទទួលបានពី Controller។

For example:

```text
1 pulse  = 1 unit of insulin
10 pulses = 10 units of insulin
```

This one-pulse/one-unit relationship is explicitly described in the case study.

---

### FR-09 — Continuous Monitoring

**English:**
The system shall continue monitoring the patient's blood sugar level.

**Khmer:**
ប្រព័ន្ធត្រូវបន្តតាមដានកម្រិតជាតិស្ករក្នុងឈាមរបស់អ្នកជំងឺ។

---

# 6. Non-Functional Requirements

Non-functional requirements describe **how the system should operate**.

## NFR-01 — Safety

**English:**
The system shall operate safely and minimize the risk of delivering an incorrect insulin dose.

**Khmer:**
ប្រព័ន្ធត្រូវដំណើរការដោយសុវត្ថិភាព និងកាត់បន្ថយហានិភ័យនៃការបញ្ចេញអាំងស៊ុយលីនខុសបរិមាណ។

---

## NFR-02 — Reliability

**English:**
The system shall reliably deliver the correct amount of insulin required for the patient's current blood sugar level.

**Khmer:**
ប្រព័ន្ធត្រូវមានភាពជឿទុកចិត្តបាន និងត្រូវបញ្ចេញអាំងស៊ុយលីនក្នុងបរិមាណត្រឹមត្រូវសម្រាប់កម្រិតជាតិស្ករបច្ចុប្បន្ន។

---

## NFR-03 — Availability

**English:**
The system shall be available to deliver insulin when required.

**Khmer:**
ប្រព័ន្ធត្រូវអាចប្រើប្រាស់បាននៅពេលដែលត្រូវការបញ្ចេញអាំងស៊ុយលីន។

---

## NFR-04 — Accuracy

**English:**
The system shall accurately calculate the required insulin dose.

**Khmer:**
ប្រព័ន្ធត្រូវគណនាបរិមាណអាំងស៊ុយលីនដែលត្រូវការបានត្រឹមត្រូវ។

---

## NFR-05 — Response Time

**English:**
The system should process sensor information and control the pump within an appropriate time.

**Khmer:**
ប្រព័ន្ធគួរដំណើរការព័ត៌មានពី Sensor និងគ្រប់គ្រង Pump ក្នុងរយៈពេលសមស្រប។

---

## NFR-06 — Fault Handling

**English:**
The system shall detect relevant error conditions and notify the user using an alarm.

**Khmer:**
ប្រព័ន្ធត្រូវរកឃើញស្ថានភាព Error ដែលពាក់ព័ន្ធ និងជូនដំណឹងដល់អ្នកប្រើប្រាស់តាមរយៈ Alarm។

The published case-study requirements identify alarms for error conditions as part of the system constraints.

---

# 7. Safety Requirements

Because the insulin pump is a **safety-critical system**, safety is one of the most important requirements.

The main safety objectives are:

1. Prevent incorrect insulin dosage.
2. Prevent excessive insulin delivery.
3. Prevent insufficient insulin delivery.
4. Detect system errors.
5. Notify the user when an error occurs.
6. Ensure reliable insulin delivery.

The case study specifically emphasizes that incorrect operation can cause serious health consequences and therefore requires reliable and safe operation.

---

# 8. Process Model

The process model describes how the system transforms sensor information into insulin pump commands.

## Main Process

```text
Start
  ↓
Blood Sensor
  ↓
Analyze Sensor Reading
  ↓
Blood Sugar
  ↓
Compute Insulin
  ↓
Insulin Dose
  ↓
Compute Pump Commands
  ↓
Pump Data
  ↓
Control Insulin Pump
  ↓
Insulin Pump
  ↓
End / Continue Monitoring
```

The original UML activity model contains the sequence:

**Blood Sensor → Analyze Sensor Reading → Blood Sugar → Compute Insulin → Insulin Dose → Compute Pump Commands → Pump Data → Control Insulin Pump → Insulin Pump**

It also includes **Insulin Log** and **Log Dose** activities.

---

# 9. Process Model Explanation

### Step 1 — Blood Sensor

The sensor measures a blood parameter related to the patient's blood sugar level.

### Step 2 — Analyze Sensor Reading

The controller analyzes the sensor information.

### Step 3 — Determine Blood Sugar

The controller determines the blood sugar level from the sensor information.

### Step 4 — Compute Insulin

The controller calculates the required amount of insulin.

### Step 5 — Determine Insulin Dose

The calculated amount becomes the required insulin dose.

### Step 6 — Compute Pump Commands

The controller converts the insulin dose into commands for the pump.

### Step 7 — Control Insulin Pump

The controller sends signals/pulses to the pump.

### Step 8 — Deliver Insulin

The insulin pump delivers the required insulin to the patient.

---

# 10. Input and Output

| Type             | Description                                      |
| ---------------- | ------------------------------------------------ |
| **Input**        | Blood sensor readings                            |
| **Processing**   | Analyze sensor reading and calculate blood sugar |
| **Processing**   | Calculate required insulin dose                  |
| **Output**       | Pump control commands                            |
| **Final Output** | Insulin delivered to patient                     |

---

# 11. System Flow

```text
┌─────────────────┐
│  Blood Sensor   │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Analyze Reading │
└────────┬────────┘
         ↓
┌─────────────────┐
│  Blood Sugar    │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Compute Insulin │
└────────┬────────┘
         ↓
┌─────────────────┐
│  Insulin Dose   │
└────────┬────────┘
         ↓
┌─────────────────────┐
│ Compute Pump Command│
└──────────┬──────────┘
           ↓
┌─────────────────┐
│ Control the Pump│
└────────┬────────┘
         ↓
┌─────────────────┐
│  Insulin Pump   │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Deliver Insulin │
└─────────────────┘
```

---

# 12. Requirements Classification

| Requirement                | Type           |
| -------------------------- | -------------- |
| Collect sensor information | Functional     |
| Analyze sensor readings    | Functional     |
| Calculate blood sugar      | Functional     |
| Calculate insulin dose     | Functional     |
| Generate pump commands     | Functional     |
| Control insulin pump       | Functional     |
| Deliver insulin            | Functional     |
| Monitor continuously       | Functional     |
| Safety                     | Non-Functional |
| Reliability                | Non-Functional |
| Availability               | Non-Functional |
| Accuracy                   | Non-Functional |
| Fault handling             | Non-Functional |

---

# 13. Key Requirements from the Original Case Study

The two most important high-level requirements identified in the original case study are:

> **1. The system shall be available to deliver insulin when required.**

> **2. The system shall perform reliably and deliver the correct amount of insulin to counteract the current level of blood sugar.**

These are the best requirements to highlight in your case study because they come directly from the published insulin pump case study.

---

# 14. Documentation Structure

This project can be organized as:

```text
Insulin Pump Control System
│
├── URD
│   ├── Introduction
│   ├── Users / Stakeholders
│   ├── Functional Requirements
│   ├── Non-Functional Requirements
│   └── Safety Requirements
│
├── Process Model
│   ├── Input
│   ├── Processing
│   └── Output
│
├── UML Activity Model
│   ├── Blood Sensor
│   ├── Analyze Sensor Reading
│   ├── Compute Insulin
│   ├── Compute Pump Commands
│   └── Control Insulin Pump
│
└── References
```

---

# 15. References

### Main Reference

**Sommerville, Ian. *Software Engineering*, 10th Edition, Pearson Education Limited, 2016.**

The Open Design Case Study repository identifies this as the source of the insulin pump case study.

### Online Case Study

[Ian Sommerville — A Personal Insulin Pump Case Study](https://software-engineering-book.com/case-studies/insulin-pump/?utm_source=chatgpt.com)

This page provides the insulin pump case study and links to supporting requirements and formal specification materials.

### Open Design Case Study Repository

[Insulin Pump — Ian Sommerville Case Study on GitHub](https://github.com/opendesigncasestudies/InsulinPump-IanSommerville?utm_source=chatgpt.com)

The repository contains the case study, architecture image, activity model image, and citation information.

### Book Reference

[Software Engineering — Insulin Pump Case Study PDF excerpt](https://staff.emu.edu.tr/alexanderchefranov/Documents/CMSE201/Spring%202026/Sommerville2016%20GlobAl_EdiTioN_Software_Engineering_TENT.pdf?utm_source=chatgpt.com)

This source shows the hardware architecture, UML activity model, and the two essential high-level requirements.

---

# 16. Important Note

This README distinguishes between **requirements explicitly stated in Sommerville's case study** and requirements that are **reasonable interpretations for a URD**.

For an academic submission, the strongest approach is:

* Cite the **original Sommerville case study**.
* Use the original two high-level requirements as your core requirements.
* Clearly label your additional FR/NFR items as requirements derived from the case study.
* Do not claim that every NFR in this README is a direct quotation from the original text.

The original case study also has a separate **Insulin Pump Requirements Specification**, which is important because the case-study page notes that the requirements specification references the formal specification and is not intended to stand alone.
