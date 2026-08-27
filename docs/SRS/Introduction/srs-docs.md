# Software Requirements Specification (SRS)
## System: Automated Insulin Pump System

### 1. Functional Requirements
* **FR-01 (Glucose Reading):** The system shall sample glucose levels every 60 seconds.
* **FR-02 (Dose Calculation):** Compute insulin dose using formula:
  $$\text{Dose} = \frac{\text{Current\_Glucose} - \text{Target\_Glucose}}{\text{Sensitivity\_Factor}}$$
* **FR-03 (Max Limit Check):** If single dose > 5.0 Units, cap delivery and trigger safety warning.

### 2. Non-Functional Requirements
* **NFR-01 (Safety):** Motor lock occurs if sensor communication drops for over 3 minutes.
* **NFR-02 (Battery):** Backup battery must support critical operations for at least 24 hours.
* **NFR-03 (Security):** Bluetooth communication must use AES-128 encryption.