# Lab 5: Static Code Analysis — IT Helpdesk Ticket Allocator

**Name:** Rohith S  
**SRN:** PES2UG24CS409  
**Section:** G  
**GitHub Repository:** [Rohith-46-s/Lab5](https://github.com/Rohith-46-s/Lab5)

---

## Overview

This repository contains the deliverables for **Lab 5: Static Code Analysis**, focused on identifying and resolving code quality, style, and security vulnerabilities in an IT helpdesk ticketing Python program (`helpdesk_system.py`). 

Using industry-standard static analysis tools—**Pylint**, **Bandit**, and **Flake8**—the codebase was diagnosed, documented, refactored, and verified to achieve top-tier maintainability and security standards.

---

## Project Structure

```text
Lab5/
│
├── helpdesk_system.py       # Cleaned and corrected program (final version)
├── issues.md                # Comprehensive issue table and fix documentation
├── reflection.md            # Answers to reflection questions
├── requirements.txt         # Analysis and development dependencies
│
├── reports/
│   ├── before/              # Pylint, Bandit, and Flake8 reports on ORIGINAL code
│   └── after/               # Pylint, Bandit, and Flake8 reports on FIXED code
│
└── outputs/                 # Program execution logs and generated tickets.json
```

---

## Getting Started & Analysis Steps

### 1. Prerequisites & Tool Installation
Ensure you have Python installed, then install the required static analysis tools:
```bash
pip install pylint bandit flake8
```

### 2. Running Initial ("Before") Analysis
Generate the pre-fix analysis reports:
```bash
pylint helpdesk_system.py > reports/before/pylint_report.txt
bandit -r helpdesk_system.py > reports/before/bandit_report.txt
flake8 helpdesk_system.py > reports/before/flake8_report.txt
```

### 3. Setting Environment Variables (Optional for Admin Actions)
To enable administrative ticket-closing features securely:
```bash
# Windows (Command Prompt / PowerShell)
set HELPDESK_ADMIN_PASSWORD=yourpassword

# macOS / Linux
export HELPDESK_ADMIN_PASSWORD="yourpassword"
```

### 4. Running the Program
```bash
python helpdesk_system.py
```

### 5. Running Post-Fix ("After") Verification
Confirm all issues have been successfully resolved:
```bash
pylint helpdesk_system.py > reports/after/pylint_report.txt
bandit -r helpdesk_system.py > reports/after/bandit_report.txt
flake8 helpdesk_system.py > reports/after/flake8_report.txt
```

---

## Summary of Results

* **Pylint Score:** Improved from **4.85/10** to **10.00/10** (zero warnings or errors).
* **Bandit Security Issues:** Eliminated all high and medium severity vulnerabilities (including hardcoded passwords and insecure deserialization).
* **Flake8 Style Violations:** Zero PEP 8 violations remaining.