# Lab 1: Grade Evaluator & Archiver

## Project Overview

This project was developed as part of the **Introduction to Python Programming and Databases** course.

The Python program (`grade-evaluator.py`) reads a student's assignment scores from a CSV file and classifies their overall performance — it checks the scores and weights are valid, calculates the final grade and GPA, and decides whether the student has passed or failed, while also flagging any formative assignments that need to be resubmitted.

Alongside it, the shell script (`organizer.sh`) keeps the workspace tidy: after grades are processed, it archives the used `grades.csv` with a timestamp and resets a fresh, empty one so the next batch of grades can be entered.

---

## Project Structure

```
Lab1/

├── grade-evaluator.py
├── organizer.sh
├── grades.csv
├── README.md
├── organizer.log          (created after running organizer.sh)
└── archive/               (created after running organizer.sh)
```

---

## Features

### Python Application (`grade-evaluator.py`)

- Reads grade records from a CSV file.
- Validates that all scores are between 0 and 100.
- Validates that:
  - Total assignment weight equals 100.
  - Formative assignments total 60%.
  - Summative assignments total 40%.
- Calculates the final grade.
- Calculates the GPA using:

```
GPA = (Final Grade / 100) × 5.0
```

- Determines whether the student has PASSED or FAILED.
- Identifies the highest-weight failed formative assignment(s) eligible for resubmission.

---

### Bash Script (`organizer.sh`)

- Creates an `archive` directory if it does not already exist.
- Generates a timestamp.
- Renames `grades.csv` using the timestamp.
- Moves the renamed file into the archive folder.
- Creates a new empty `grades.csv`.
- Records every archive operation in `organizer.log`.

---

## Requirements

- Python 3
- Bash Shell (Linux, macOS, or WSL on Windows)

---

## How to Run the Python Program

Open a terminal in the project directory and run:

```bash
python3 grade-evaluator.py
```

When prompted, enter the CSV filename:

```
grades.csv
```

Alternatively, skip the prompt by passing the filename directly as an argument:

```bash
python3 grade-evaluator.py grades.csv
```

The program will:

- Validate that every score is between 0 and 100
- Validate that total, formative, and summative weights match the required rules
- Calculate the final grade and GPA
- Display the student's PASS/FAIL status
- List any failed formative assignments and flag the highest-weight one(s) as eligible for resubmission

---

## How to Run the Shell Script

Give the script execute permission:

```bash
chmod +x organizer.sh
```

Run the script:

```bash
./organizer.sh
```

Example output:

```
Archived 'grades.csv' as 'archive/grades_20260725-184010.csv'.
A new empty 'grades.csv' has been created for the next batch of grades.
Logged operation to organizer.log.
```

The script will:

- Archive the current `grades.csv` with a timestamped filename
- Move it into the `archive/` directory
- Create a new empty `grades.csv`
- Record the operation in `organizer.log`

---

## Author

Name: GAYAWIRA LUXE Gaultier
