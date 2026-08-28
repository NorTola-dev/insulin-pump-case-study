# 🩸 Automated Insulin Pump System — Software Engineering Case Study

[Domain: Software Engineering] | [System: Safety-Critical] | [Process: V-Model/Agile] | [Git: GitFlow]

This repository contains the full Software Engineering Case Study for an Automated Insulin Pump System. The project covers the end-to-end software development lifecycle for a safety-critical medical device, including User Requirements Document (URD), Software Requirements Specification (SRS), System Architecture, and Software Process Modeling.

---

## 📌 1. Executive Summary

An Automated Insulin Pump System is a wearable medical IoT device designed to monitor blood glucose levels continuously and deliver insulin doses safely to Type 1 Diabetes patients. Because an overdose or underdose can be life-threatening, this software is classified as a Safety-Critical System, requiring strict verification, validation, and fault-tolerant architecture.

### Key Objectives
* Define complete User Requirements (URD) for patients and healthcare professionals.
* Detail technical Software Requirements (SRS) adhering to safety standards (e.g., Ian Sommerville SE standards & FDA guidance).
* Structure system execution using a V-Model / Agile Hybrid Process Model.
* Demonstrate collaborative software engineering practices using GitFlow among an 8-member team.

---

## 📁 2. Repository Folder Structure

```
Insulin-Pump---Case-Study/
│
├── README.md
├── .gitattributes
│
├── docs/
│   ├── Overview/
│   │   └── overview.md
│   │
│   ├── Process-Model/
│   │   └── process_model.md
│   │
│   ├── URD/
│   │   ├── Introduction/
│   │   │   └── urd-docs.md
│   │   ├── User-Profiles/
│   │   └── Requirements/
│   │
│   └── SRS/
│       ├── Introduction/
│       │   └── srs-docs.md
│       ├── Functional/
│       └── Non-Functional/
│
└── diagrams/                       # System UML diagrams (Use Case, Sequence, State Machine)
    ├── use-case-diagram.png
    ├── sequence-diagram.png
    └── state-machine.png

```

## 🚀 3. Git Essentials Guide (Clone, Pull & Push)

All team members must follow these standard steps to set up and contribute to the repository.

📥 3.1 How to Clone the Repository
Run this command on your machine only once when joining the project:

# 1. Clone the project repository
<<<<<<< HEAD
git clone https://github.com/insulin-pump-case-study/Insulin-Pump---Case-Study.git
=======

```
git clone https://github.com/insulin-pump-case-study/Insulin-Pump---Case-Study.git
```
>>>>>>> eab74be521ebe2bfffee9732821446442718f472

# 2. Enter the project directory
```
cd Insulin-Pump---Case-Study
```

# 3. Check existing branches
```
git branch -a
```

🔄 3.2 How to Pull (Get Latest Updates)
Before starting any work, always pull the latest changes from the develop branch to prevent code conflicts:

# 1. Switch to the develop branch
```
git checkout develop
```

# 2. Pull the latest code/documents from GitHub
```
git pull origin develop
```

Pro Tip: If you are currently working inside a Feature Branch, update it with develop using:
```
git checkout feature/your-task-name
git pull origin develop
```

📤 3.3 How to Push (Upload Your Work)
Never push directly to main or develop. Always create a Feature Branch, commit your work, and push it up.

Step 1: Create a new Feature Branch
```
git checkout develop
git pull origin develop
git checkout -b feature/your-task-name
```

Step 2: Make changes, then Stage and Commit
# Check modified files
```
git status
```

# Add files to Staging Area
```
git add .
```

# Commit with a clear, descriptive message
```
git commit -m "Add SRS functional requirements section FR-01"
```

Step 3: Push to GitHub
# First-time push for a new branch:
```
git push -u origin feature/your-task-name
```

# Subsequent pushes on the same branch:
```
git push
```

Step 4: Create a Pull Request (PR)
1. Go to insulin-pump-case-study/Insulin-Pump---Case-Study on GitHub.
2. Click Compare & pull request.
3. Set Base: develop <-- Compare: feature/your-task-name.
4. Request a review from the Git Lead to merge your work.

kskdfjas

sd

nsn 3

4