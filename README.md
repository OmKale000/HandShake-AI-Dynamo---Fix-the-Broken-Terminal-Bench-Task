# HandShake AI - Dynamo: Fix the Broken Terminal-Bench Task

This repository contains my repaired version of the **Dynamo - Fix the Broken Terminal-Bench Task** assessment.

## Overview

The objective of this assessment was to diagnose and repair a broken **Terminal-Bench 2 (Harbor)** task by identifying configuration, environment, verifier, and instruction issues until the task passed Harbor validation.

## Task Summary

The task parses an Apache access log and generates a JSON summary report containing:

- Total number of requests
- Number of unique client IP addresses
- Most frequently requested path

Output:

```
/app/report.json
```

---

## Issues Identified

The following defects were identified and corrected:

- Fixed `task.toml`
  - Changed `artifacts` from a string to an array.
  - Corrected the output artifact path.

- Fixed Docker environment
  - Updated the Dockerfile.
  - Removed the leaked reference solution from the build context.

- Improved task instructions
  - Rewrote `instruction.md` to clearly define success criteria.

- Improved verifier
  - Replaced existence-only checks with validation of actual JSON values.
  - Ensured reward generation follows Harbor requirements.

- Fixed verifier execution
  - Updated `tests/test.sh` to correctly execute the verifier and generate rewards.

---

## Repository Structure

```
log-report/
├── environment/
│   ├── Dockerfile
│   └── access.log
├── solution/
│   ├── solve.py
│   └── solve.sh
├── tests/
│   ├── test_outputs.py
│   └── test.sh
├── instruction.md
└── task.toml
```

---

## Validation Results

The repaired task was validated using Harbor.

### Oracle Agent

```bash
harbor run -p log-report -a oracle
```

Result

```
Reward = 1.0
```

### NOP Agent

```bash
harbor run -p log-report --agent nop
```

Result

```
Reward = 0.0
```

These results confirm that:

- A correct solution receives full reward.
- A no-op agent correctly fails the verifier.

---

## Technologies Used

- Harbor (Terminal-Bench 2)
- Docker
- Python
- PyTest

---

## Author

**Om Anil Kale**

GitHub: https://github.com/OmKale000
