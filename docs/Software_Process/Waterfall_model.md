# Waterfall Model - Insulin Pump Case Study

## 1. Overview

**Waterfall Model** គឺជា Software Process Model ដែលអភិវឌ្ឍ System តាមលំដាប់ជំហានច្បាស់ៗ។
រាល់ Phase ត្រូវបញ្ចប់មុននឹងទៅ Phase បន្ទាប់។

Main phases:
1. Requirements
2. Design
3. Implementation and Unit Testing
4. Integration and System Testing
5. Operation and Maintenance

Waterfall មាន Structure ច្បាស់ ងាយស្រួល Plan, Manage និង Review។ សម្រាប់ **Insulin Pump** ដែលជា safety-critical system វាជួយឱ្យ Team ធ្វើការ និងរក្សា Documentation បានច្បាស់។

---

## 2. Why Use Waterfall for Insulin Pump?

Insulin Pump ជា Medical Device ដែលមាន Software គ្រប់គ្រងការផ្តល់ Insulin។ បើ Software មាន Error អាចប៉ះពាល់ដល់ Patient Safety។

ដូច្នេះ System ត្រូវការ:
- Clear and testable Requirements
- Careful Design
- Step-by-step Development
- Systematic Testing
- Good Documentation
- Controlled Changes

Waterfall ជួយឱ្យការងារមានលំដាប់ច្បាស់។ ប៉ុន្តែ Safety-critical system ក៏ត្រូវមាន **Verification, Validation, Risk Management និង Traceability** ផងដែរ។

---

## 3. How Waterfall Is Applied

### 3.1 Requirements

ក្នុង Phase នេះ Team កំណត់ថា Insulin Pump ត្រូវធ្វើអ្វីខ្លះ។ Requirements ត្រូវសរសេរឱ្យ Clear និង Testable។

Examples:
- System shall read Blood Glucose data from Sensor.
- System shall calculate Insulin Dose.
- System shall control Insulin Delivery.
- System shall detect abnormal conditions.
- System shall generate an Alarm when a serious problem occurs.
- System shall prevent an unsafe Dose.

Requirements ក្នុង Case Study មានដូចជា **SRS-FR-01 to SRS-FR-07, SRS-SR-01, SRS-SR-02 និង SRS-NFR-03**។

**Deliverables:** URD, SRS, Functional Requirements, Safety Requirements និង Traceability Record។

### 3.2 Design

ក្នុង Phase នេះ Requirements ត្រូវបានបម្លែងទៅជា System និង Software Design។ Design បង្ហាញពី Components, Interfaces និង Data Flow។

```text
Sensor / Patient Data
        |
Sensor Data Check
        |
Blood Glucose Calculation
        |
Insulin Dose Calculation
        |
Safety Check
        |
Pump Control
        |
Insulin Delivery
```

**Deliverables:** System Architecture, Software Design, Interfaces និង Data-flow Diagram។

### 3.3 Implementation and Unit Testing

Developer សរសេរ Code តាម Design ដែលបាន Approve។ Component នីមួយៗត្រូវ Test ដាច់ដោយឡែក។

Examples:
- Test Dose Calculation
- Test Sensor Data Check
- Test Safety Check
- Test Alarm Function
- Test Pump Control

**Deliverables:** Source Code, Unit Test Cases និង Unit Test Results។

### 3.4 Integration and System Testing

បន្ទាប់ពី Components នីមួយៗ Test បានល្អ វាត្រូវបាន Combine ហើយ Test ជាមួយគ្នា។

```text
Sensor
   +
Dose Calculation
   +
Safety Check
   +
Pump Control
        |
Complete Insulin Pump System
        |
System Testing
```

Testing ត្រូវ Check ថា System ធ្វើតាម Requirements ឬអត់ ហើយត្រូវ Check Safety, Error Conditions និង Performance ផងដែរ។

**Deliverables:** Integration Test Cases, System Test Cases, Test Report និង Requirements-to-Test Traceability។

### 3.5 Operation and Maintenance

បន្ទាប់ពី System Pass Testing ហើយត្រូវបាន Release វាចូលទៅ Operation និង Maintenance។

Maintenance អាចមាន:
- Fix Software Bugs
- Fix Defects
- Update System when approved
- Update Documentation
- Update Requirements and Tests when needed

សម្រាប់ Medical Device ការផ្លាស់ប្តូរ ត្រូវ Control និង Test មុនពេល Release។

**Deliverables:** Maintenance Records, Updated Documents, Change Records និង Regression Test Results។

---

## 4. Example: Insulin Dose Safety

ចំណុចសំខាន់មួយគឺ System មិនត្រូវផ្តល់ Insulin Dose ដែលមិនមានសុវត្ថិភាព។

Example:

```text
Maximum Safe Dose = 10 units
Calculated Dose   = 15 units
```

System ត្រូវធ្វើ **Safety Check** មុនពេល Delivery:

```text
Calculated Dose
       |
Safety Check
       |
15 > 10
       |
Prevent Unsafe Delivery
       |
Generate Alarm
```

នេះមានន័យថា System ត្រូវ Stop ការផ្តល់ Dose ដែលលើស Limit និងបង្ហាញ Alarm។ វាជួយ Prevent Unsafe State និងការពារ Patient Safety។

---

## 5. Key Strengths

### 5.1 Clear Structure

រាល់ Phase មានការងារច្បាស់លាស់ ដូច្នេះ Team ងាយដឹងថាត្រូវធ្វើអ្វីមុន និងអ្វីក្រោយ។

### 5.2 Clear Requirements

Requirements ត្រូវបានកំណត់មុន Coding ហើយអាច Review មុនចូល Phase បន្ទាប់។

### 5.3 Good Documentation

រាល់ Phase មាន Documents និង Deliverables ដែលអាច Review និង Trace បាន។

### 5.4 Systematic Testing

Testing ត្រូវបាន Plan ជាមុន ហើយអាច Link ជាមួយ Requirements។

### 5.5 Easy to Manage

Process ដែលមានលំដាប់ច្បាស់ ធ្វើឱ្យ Project Planning និង Progress Tracking ងាយស្រួល។

---

## 6. Limitations

### 6.1 Difficult to Change Requirements

បើ Requirements ផ្លាស់ប្តូរនៅពេល Development បានចាប់ផ្តើម វាអាចធ្វើឱ្យត្រូវកែ Design, Code និង Tests ម្តងទៀត។

Example:

```text
Original Requirement
Maximum Dose = 10 units
        |
Design
        |
Implementation
        |
New Requirement
Maximum Dose = 8 units
```

ការផ្លាស់ប្តូរបែបនេះអាចបង្កើត **Rework** និងចំណាយពេលបន្ថែម។

### 6.2 Feedback Can Come Late

User អាចមិនឃើញ Complete System រហូតដល់ចុង Development។ ដូច្នេះ Problem ខ្លះអាចរកឃើញយឺត។

### 6.3 Late Changes Can Be Expensive

បើ Requirement ផ្លាស់ប្តូរយឺត អាចត្រូវ Update Design, Code និង Test Cases ជាច្រើន។

---

## 7. Waterfall and V-Model

**V-Model** មានគំនិតស្រដៀង Waterfall ព្រោះទាំងពីរមាន Planned និង Structured Process។

- **Waterfall** ផ្តោតលើ Development Steps តាមលំដាប់។
- **V-Model** ផ្តោតលើ Development និង Testing ដែលភ្ជាប់គ្នា។

Example:

```text
Requirements Specification  <->  Acceptance Testing
System Specification       <->  System Testing
Architecture Design        <->  Integration Testing
Detailed Design            <->  Unit Testing
             \              /
              Implementation
```

សម្រាប់ Insulin Pump, V-Model អាចជួយបន្ថែម **Testing និង Traceability** ទៅក្នុង Waterfall Process។

---

## 8. Waterfall Phase Summary

| Phase | Main Activity | Main Deliverable |
|---|---|---|
| Requirements | កំណត់ System និង Safety Needs | URD / SRS |
| Design | រៀបចំ Architecture និង Software Modules | Design Documents |
| Implementation | សរសេរ និង Develop Code | Source Code |
| Testing | Test និង Verify System | Test Cases / Test Report |
| Operation & Maintenance | Run, Fix និង Update System | Maintenance Records |

---

## 9. Summary

**Waterfall Model** គឺជា Process Model ដែលមានលំដាប់ច្បាស់៖

```text
Requirements
     |
Design
     |
Implementation
     |
Testing
     |
Operation & Maintenance
```

សម្រាប់ **Insulin Pump Case Study**, Waterfall ជួយ Team រៀបចំ Requirements, Design, Coding, Testing និង Documentation ឱ្យមាន Order ច្បាស់។

ដោយសារ Insulin Pump ជា **Safety-critical Medical System**, Team ត្រូវយកចិត្តទុកដាក់លើ Safety, Verification, Validation, Risk Management និង Requirements Traceability។

**V-Model** អាចប្រើជាមួយ Waterfall ដើម្បីធ្វើឱ្យ Testing និង Traceability កាន់តែច្បាស់។

## 10. References

- Sommerville, I. *Software Engineering*, 10th Edition.
- Software Process Models and Activities, Chapter 2.
- Insulin Pump Case Study - Safety and Software Requirements.
