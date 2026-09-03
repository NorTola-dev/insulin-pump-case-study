# V-Model – Insulin Pump Case Study

## 1. Overview

The V-Model is a software process model that connects development activities with testing activities.

It is useful for safety-critical systems because testing is planned from the beginning.

For the insulin pump case study, the V-Model can be used after the main requirements and system architecture have been reviewed and approved.

The main idea is simple:

- The left side defines and designs the system.
- The bottom is implementation.
- The right side verifies and validates the system.

This creates a clear link between requirements, design, implementation, and testing.

## 2. V-Model Workflow

```text
Requirements                              Acceptance Testing
      ↓                                         ↑
System Requirements                        System Testing
      ↓                                         ↑
System Architecture                      Integration Testing
      ↓                                         ↑
Detailed Design                             Unit Testing
      ↓                                         ↑
      └──────────── Implementation ────────────┘
```

Each development activity has a related testing activity.
## 3. How V-Model is Applied to the Insulin Pump

### 3.1 User Requirements

First, the team defines what users need from the insulin pump.

Examples:

- The pump should deliver insulin when required.
- The pump should detect abnormal conditions.
- The pump should give an alarm for serious problems.
- The pump should help prevent an unsafe insulin dose.

**Deliverable:** User Requirements Document (URD)

**Related test:** Acceptance Testing

### 3.2 System and Software Requirements

The user needs are converted into clear software requirements.

Examples from the case study include:

- **SRS-FR-01:** Sensor Data Acquisition
- **SRS-FR-04:** Insulin Dose Calculation
- **SRS-SR-01:** Overdose Prevention
- **SRS-NFR-03:** Execution Time requirement

Each requirement should be clear, testable, and traceable.

**Deliverable:** Software Requirements Specification (SRS)

**Related test:** System and Safety Testing
### 3.3 System Architecture and Detailed Design

The team designs the system structure and the main software modules.

For example:

```text
Sensor Data
    ↓
Glucose Processing
    ↓
Dose Calculation
    ↓
Safety Check
    ↓
Pump Control
```

The detailed design explains how each module works and how the modules communicate.

**Deliverable:** System Architecture and Detailed Design Documents

**Related test:** Integration Testing and Unit Testing

### 3.4 Implementation and Unit Testing

Developers write the software based on the approved design.

Each module is tested separately before it is combined with other modules.

Examples:

- Test the glucose calculation function.
- Test the insulin dose calculation function.
- Test the safety check function.
- Test the alarm function.

**Deliverable:** Source Code and Unit Test Results

**Related test:** Unit Testing

### 3.5 Integration Testing

After unit testing, the software modules are combined and tested together.

For example:

```text
Sensor
  +
Glucose Processing
  +
Dose Calculation
  +
Safety Check
  +
Pump Control
       ↓
Integrated System
```

The goal is to check whether the modules communicate and work correctly together.

**Deliverable:** Integration Test Report

**Related requirement:** Sensor, dose calculation, safety, and pump control requirements
### 3.6 System and Safety Testing

The complete system is tested against the SRS and safety requirements.

Important checks include:

- The pump must not deliver a dose above the defined safety limit.
- Hardware or software faults should be detected when possible.
- Serious problems should trigger an appropriate safety response.
- The software should meet its required response time.

For example, **SRS-SR-01** can be tested to check that an unsafe dose is blocked.

**Deliverable:** System and Safety Test Report

**Related test:** System Testing

### 3.7 Acceptance Testing

The final system is checked against the original user requirements.

The purpose is to confirm that the system meets the expected user needs and works correctly in defined clinical scenarios or a suitable simulator.

**Deliverable:** Acceptance Test Report

**Related requirement:** User Requirements Document (URD)

## 4. Key Strengths

### 4.1 Clear Testing Plan

Testing is planned together with development, so important tests are not forgotten.

### 4.2 Good Traceability

A requirement can be linked to its design, implementation, and test case.

### 4.3 Useful for Safety-Critical Software

The structured process supports careful verification and validation of important safety functions.

### 4.4 Easy to Review

Each stage has clear documents, activities, and test results that can be reviewed.

## 5. Limitations

### 5.1 Changes Can Be Expensive

Large requirement changes may affect design, code, and test cases.

### 5.2 Less Flexible Than Iterative Models

The V-Model is more structured than models that allow frequent changes during development.

### 5.3 Requires Good Requirements

If an important requirement is missing or unclear, later design and testing may also be affected.
## 6. V-Model and Waterfall Model

Both models use a structured development approach, but they emphasize different things.

| Waterfall Model | V-Model |
|---|---|
| Shows the sequence of development stages | Connects development stages with testing stages |
| Testing is a later development activity | Testing is planned from the beginning |
| Focuses on a step-by-step process | Focuses on verification and validation |

For the insulin pump case study:

**Waterfall →** provides a clear sequence of development activities.

**V-Model →** adds a stronger connection between each development activity and its related testing activity.

## 7. Summary

The V-Model provides a structured way to develop and test the insulin pump software.

The main flow is:

```text
User Requirements
       ↓
System Requirements
       ↓
System Design
       ↓
Detailed Design
       ↓
Implementation
       ↓
Unit Testing
       ↓
Integration Testing
       ↓
System & Safety Testing
       ↓
Acceptance Testing
```

For a safety-critical medical system, clear requirements, careful design, systematic testing, and traceability are very important.

The V-Model helps the team connect these activities in a clear and organized way.

## 8. References

- Sommerville, I. *Software Engineering*, 10th Edition.
- Software Process Models and Activities, Chapter 2.
- Insulin Pump Case Study – Safety and Software Requirements.
