
## 1. Overview & Operational Scope
**Spiral Model** គឺជា Risk-Driven Process Model ដែលត្រូវបានយកមកប្រើប្រាស់ **នៅដំណាក់កាលដំបូងនៃការអភិវឌ្ឍ (Early Research, Concept Feasibility, & Hazard Analysis)** របស់ Insulin Pump Control System។

វាត្រូវបានអនុវត្តដើម្បី **ស្វែងរក វិភាគ និងលុបបំបាត់ហានិភ័យ (Hazard & Risk Management)** ព្រមទាំងតេស្តផ្ទៀងផ្ទាត់ Algorithm និង Hardware Prototypes ច្រើនសារឡើងវិញ (Iterative Cycles) មុនពេល Lock/Freeze Requirements សម្រាប់ផ្ទេរទៅឱ្យ V-Model ធ្វើការផលិតផ្លូវការ។

---

## 2. Four Quadrants of Spiral Iterations

នៅក្នុង Spiral Loop នីមួយៗ ការងារត្រូវឆ្លងកាត់ ៤ ជ្រុង (Quadrants) ជាបន្តបន្ទាប់៖

```text
               1. Determine Objectives & Constraints
                                 |
         +-----------------------+-----------------------+
         |                                               |
         v                                               v
 4. Plan Next Phases                            2. Risk Analysis & Prototyping
 (Pass to V-Model when clear)                   (Hazard Analysis ISO 14971)
         ^                                               |
         |                                               v
         +-----------------------+-----------------------+
                                 |
                 3. Engineering & Evaluation
```

---

## 3. Where & How Spiral Model is Applied in Insulin Pump

| Quadrant Name | Core Activities | Specific Insulin Pump Application |
| :--- | :--- | :--- |
| **1. Determine Objectives** | កំណត់គោលដៅ លក្ខខណ្ឌកម្រិត និង Boundaries | កំណត់ Target Glucose Levels, Pump Delivery Limitations |
| **2. Risk Analysis & Prototyping** | វិភាគ Hazard/Risks និងបង្កើត Rapid Prototypes | **Hazard Analysis (ISO 14971):** ចុះបើ Sensor អានខុស? ចុះបើ Battery ជិតអស់? <br>**Prototyping:** បង្កើត Math Simulation លើ MATLAB សម្រាប់ Sensor Filter Algorithm (**SRS-FR-02**) |
| **3. Engineering & Evaluation** | តេស្ត Evaluated Prototypes និងកែសម្រួល Algorithm | សាកល្បង Insulin Dose Calculation Logic ជាមួយទិន្នន័យជាតិស្ករសប្បនិម្មិត (Simulated Datasets) |
| **4. Plan Next Phases** | វាយតម្លៃលទ្ធផល រៀបចំផែនការ Spiral Loop បន្ទាប់ | ប្រសិនបើ Risk ទាំងអស់ត្រូវកាត់បន្ថយដល់កម្រិតសុវត្ថិភាព នោះ Requirements នឹងត្រូវ Freeze ហើយផ្ទេរទៅ **V-Model** |

---

## 4. Key Strengths in Insulin Pump Context
1. **Prototyping Complex Algorithms:** អនុញ្ញាតឱ្យតេស្ត និងកែសម្រួល Sensor Noise Filtering និង Dose Calculation Algorithms ដោយសុវត្ថិភាពលើ Simulation Model។
2. **Hazard Mitigation (ISO 14971):** ធានាថារាល់ Hazard (ដូចជា Overdose, Hardware Freeze, Noise Anomaly) ត្រូវបានស្វែងរក និងបង្កើត Safety Guardrails (SRS-SR-01, SRS-SR-02) ត្រឹមត្រូវ មុននឹងសរសេរ Production Code។

---

## 5. Summary: Co-existence of V-Model & Spiral Model

```text
 [Phase 1: Research & Risk Management]          [Phase 2: Formal Engineering & Compliance]
 
           Spiral Model                                           V-Model
   (Prototypes & Risk Identification)                  (Formal Build, Verification & Audit)
            
                   |                                                 ^
                   |                                                 |
                   +---> [Freeze Requirements & Architecture] -------+