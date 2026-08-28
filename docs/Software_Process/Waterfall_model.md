# Waterfall Model – Insulin Pump Case Study

## 1. Overview

The Waterfall Model is a plan-driven software process model.
It develops software through a sequence of clearly defined stages.

The main stages are:

1. Requirements Analysis and Definition
2. System and Software Design
3. Implementation and Unit Testing
4. Integration and System Testing
5. Operation and Maintenance

Each stage produces results that are used in the next stage.

The Waterfall Model is suitable for critical systems and embedded systems.


## 2. Why Waterfall is Suitable for Insulin Pump

An insulin pump is a software-controlled medical device.
It is a safety-critical system because software failure can affect the patient's health.

Therefore, the development process needs:

- Clear requirements
- Careful system design
- Well-defined development steps
- Testing and validation
- Good documentation
- Maintenance after deployment

The Waterfall Model provides a structured and plan-driven process that can support these needs.


## 3. Where and How Waterfall is Applied in the Insulin Pump

The Waterfall Model can be applied to the insulin pump as follows.


### 3.1 Requirements Analysis and Definition

In this stage, we define what the insulin pump must do.

Examples:

- The system shall calculate the required insulin dose.
- The system shall control insulin delivery.
- The system shall detect abnormal conditions.
- The system shall generate an alarm when a serious problem occurs.
- The system shall prevent an unsafe insulin dose.


### 3.2 System and Software Design

In this stage, the requirements are converted into a system design.

For example:

```text
Sensor / Patient Data
        ↓
Dose Calculation
        ↓
Safety Check
        ↓
Pump Control
        ↓
Insulin Delivery

The design defines how the software components work together.

3.3 Implementation and Unit Testing

In this stage, developers implement the software based on the design.

Each software component is tested separately.

For example:

Dose Calculation
       ↓
Unit Test

Safety Check
       ↓
Unit Test

Alarm System
       ↓
Unit Test
3.4 Integration and System Testing

After testing individual components, the components are combined.

For example:

Sensor
   +
Dose Calculation
   +
Safety Check
   +
Pump Control
        ↓
Complete Insulin Pump System
        ↓
System Testing

The complete system is tested to check whether it meets the requirements.

3.5 Operation and Maintenance

After the system passes testing and is deployed, it enters operation.

Maintenance may include:

Fixing software problems
Correcting errors
Improving the system
Updating requirements when necessary
4. Example: Insulin Dose Safety

One important safety requirement is that the pump should not deliver an unsafe insulin dose.

For example:

Maximum Safe Dose = 10 units
Calculated Dose    = 15 units

The system should perform a safety check:

Calculated Dose
       ↓
Safety Check
       ↓
15 > 10
       ↓
Prevent Unsafe Delivery
       ↓
Generate Alarm / Safety Response

The purpose is to prevent the system from reaching an unsafe state.

This example shows why clear requirements, careful design, implementation, and testing are important for an insulin pump.

5. Key Strengths in the Insulin Pump Context
5.1 Clear Structure

The development process has clearly defined stages.

5.2 Clear Requirements

Requirements are defined before implementation.

5.3 Good Documentation

Each stage can produce documents and deliverables that can be reviewed.

5.4 Supports Systematic Testing

Testing is planned as part of the development process.

5.5 Suitable for Critical and Embedded Systems

The Waterfall Model is identified as suitable for critical systems and embedded systems.

6. Limitations

The Waterfall Model also has some limitations.

6.1 Difficult to Handle Changes

Changing requirements after development has started can be difficult.

For example:

Original Requirement
Maximum Dose = 10 units
        ↓
Design
        ↓
Implementation
        ↓
New Requirement
Maximum Dose = 8 units

The change may require updates to the requirements, design, software, and tests.

This can cause rework.

6.2 Feedback Can Come Late

Users may not see the complete system until later in the development process.

7. Waterfall and V-Model

The V-Model can be used together with a plan-driven development process.

Waterfall mainly shows the sequence of development stages.

The V-Model shows the relationship between development activities and testing activities.

For example:

Requirements Specification
            ↕
       Customer Test

System Specification
            ↕
   System Integration Test

Subsystem Design
            ↕
Subsystem Integration Test

Component Design
            ↕
   Component Code & Test

Therefore:

Waterfall → organizes the development process.
V-Model → connects development activities with testing activities.
8. Summary

The Waterfall Model is a plan-driven software process model.

For the Insulin Pump case study, it provides a structured development process:

Requirements
     ↓
Design
     ↓
Implementation
     ↓
Testing
     ↓
Operation & Maintenance

Because the insulin pump is a critical embedded medical system, clear requirements, careful design, systematic testing, and validation are important.

The V-Model complements the Waterfall approach by connecting development stages with their related testing activities.

9. References
Sommerville, I. Software Engineering, 10th Edition.
Software Process Models and Activities, Chapter 2.
Insulin Pump Case Study – Safety and Software Requirements.