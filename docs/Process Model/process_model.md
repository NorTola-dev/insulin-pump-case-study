# Process Model – Insulin Pump Case Study

## 1. Introduction

The insulin pump is a software-controlled medical device that delivers controlled
doses of insulin to people with diabetes.

The insulin pump is a **safety-critical system** because a failure of the system
can cause injury or even death to the user. Therefore, software development for
the insulin pump must place strong emphasis on safety, reliability, verification,
validation, and systematic documentation.

A software process is a set of activities involved in developing and maintaining
software. The fundamental software process activities are:

1. Software specification
2. Software development
3. Software validation
4. Software evolution

A **software process model** is a simplified representation of a software
process. Different process models represent different approaches to software
development.

---

## 2. Selected Process Model

### Plan-Driven Waterfall Model

The selected process model for the insulin pump is the **Plan-Driven Waterfall
Model**.

The Waterfall model represents software development as a sequence of separate
phases. The main activities are:

1. Requirements specification
2. Software design
3. Implementation
4. Testing
5. Operation and maintenance

For safety-critical software, the development process generally follows a
plan-based Waterfall model with reviews and checks at each stage. Fault
avoidance and fault detection are important drivers of the process.

---

## 3. Why Waterfall is Suitable for the Insulin Pump

The insulin pump requires a highly structured development process because
software failure may result in serious consequences for the patient.

Some possible hazards include:

- Insulin overdose
- Insulin underdose
- Hardware monitoring failure
- Battery or power failure
- Sensor failure
- Timer failure
- Incorrect insulin dose calculation
- Incorrect timing of insulin delivery

The Waterfall model is suitable because it provides:

- Detailed requirements before implementation
- Clearly defined development phases
- Systematic documentation
- Reviews and checks at each stage
- Verification and validation activities
- Controlled development
- Traceability between requirements and testing

Therefore, a plan-driven Waterfall process is appropriate for the Insulin Pump
case study.

---

## 4. Process Model Overview

The development process for the Insulin Pump can be represented as follows:

```text
Requirements Specification
            │
            ▼
System and Software Design
            │
            ▼
Implementation
            │
            ▼
Integration and Testing
            │
            ▼
System Validation
            │
            ▼
Operation and Maintenance

---

