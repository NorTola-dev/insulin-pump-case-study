
## 1. Overview & Operational Scope
**V-Model** គឺជា Process Model ចម្បងដែលត្រូវបានប្រើប្រាស់សម្រាប់ការអភិវឌ្ឍផ្នែក **Formal Engineering, Implementation, និង Testing/Compliance Validation** របស់ Insulin Pump Control System។ 

វាត្រូវបានយកមកអនុវត្ត **នៅពេលដែល Requirements និង System Architecture ត្រូវបាន Freeze (កំណត់ច្បាស់លាស់ ១០០%)** ចេញពីដំណាក់កាល Research & Risk Analysis ដើម្បីធានាបាននូវ Bi-directional Traceability តាមស្តង់ដារវេជ្ជសាស្ត្រ **IEC 62304 Class C** និង **FDA Software Validation Guidelines**។

---

## 2. Structural Workflow & Mapping

V-Model បែងចែកការងារជាពីរផ្នែកធំៗ គឺ **Verification (កៀបចុះខាងឆ្វេង)** និង **Validation (ឡើងលើខាងស្តាំ)** ៖

```text
    [Verification Phase]                                        [Validation Phase]

  1. User Requirements (URD) -----------------------------> 8. User Acceptance Testing (UAT)
           \                                                       ^
            v                                                     /
  2. System / SRS Requirements -------------------------> 7. System & Safety Testing
           \                                                       ^
            v                                                     /
  3. Architecture Design -------------------------------> 6. Subsystem / Integration Testing
           \                                                       ^
            v                                                     /
  4. Detailed Module Design ----------------------------> 5. Unit Testing
           \                                                       ^
            v                                                     /
             +---------------------------------------------------+
             |            Implementation & Code Freeze           |
             +---------------------------------------------------+
```

---

## 3. Where & How V-Model is Applied in Insulin Pump

| Phase Number & Name | Activities & Deliverables | Specific Insulin Pump Component / Requirement |
| :--- | :--- | :--- |
| **1. User Requirements (URD)** | កំណត់តម្រូវការរបស់អ្នកជំងឺ និងគ្រូពេទ្យ | កំណត់ការចាក់ថ្នាំតាម Sensor, Safety Overdose Limits |
| **2. SRS Requirements** | បង្កើតឯកសារ SRS-FR (01-07) និង SRS-SR (01-02) | **SRS-FR-04** (Dose Calc), **SRS-SR-01** ($D_{max}$ Clamp) |
| **3. Architecture Design** | រៀបចំ Hardware/Software Interfaces & Data Flow | Real-Time OS Scheduler, Control Loop Interface |
| **4. Detailed Module Design** | ឌីសាញ Algorithm Logic និង Math Equations | Floating-point conversion formulas, GPIO Driver Logic |
| **5. Unit Testing** | តេស្ត Class, Function, និង Driver នីមួយៗដាច់ដោយឡែក | ផ្ទៀងផ្ទាត់ Function គណនាជាតិស្ករ និង Dose Calculation |
| **6. Integration Testing** | តេស្តការតភ្ជាប់រវាង Module និង Hardware Subsystems | ផ្ទៀងផ្ទាត់ការបញ្ជូន Pulse Signal ពី Software ទៅ Pump Motor |
| **7. System & Safety Testing** | តេស្តសុវត្ថិភាព និងការឆ្លើយតបពេលវេលាជាក់ស្តែង (Real-Time) | ផ្ទៀងផ្ទាត់ **SRS-NFR-03** ($T_{exec} \le 500	ext{ ms}$) និង **SRS-SR-01** ($D_{max}$) |
| **8. Acceptance Testing (UAT)** | ផ្ទៀងផ្ទាត់ប្រព័ន្ធទាំងមូលជាមួយ Clinical Scenarios | ធ្វើការតេស្តលំហូរការងារចាក់ថ្នាំជាមួយ Clinical Simulator |

---

## 4. Key Strengths in Insulin Pump Context
1. **Strict Traceability:** រាល់ Test Case ក្នុង System Safety Testing អាច Trace ត្រឡប់មក SRS-SR-01 និង SRS-FR-04 វិញបានយ៉ាងច្បាស់លាស់។
2. **Regulatory Compliance:** ឆ្លើយតប ១០០% ទៅនឹងលក្ខខណ្ឌតម្រូវនៃសវនកម្ម (Audit) របស់ FDA និង IEC 62304។