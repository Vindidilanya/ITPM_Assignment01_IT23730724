# IT3040 – IT Project Management | Assignment 1
## BSc (Hons) in Information Technology – Year 3 | Semester 1
### Option 1: Transliteration Accuracy Testing

---

## Assignment Overview

| Detail | Info |
|---|---|
| Module | IT3040 – IT Project Management (ITPM) |
| Year / Semester | Year 3, Semester 1 |
| Option | Option 1 – Transliteration Accuracy Testing |
| Student ID | IT23730724 |
| Submission Date | 4th May |

---

## Objective

Evaluate how accurately the **Chat Sinhala** transliteration function at [pixelssuite.com/chat-translator](https://www.pixelssuite.com/chat-translator) converts chat-style Singlish input into Sinhala output.

Fifty negative test cases are automated using Playwright, covering all **24 Singlish input types** defined in Appendix 1 of the assignment brief (minimum 2 test cases per input type). All test case IDs begin with `Neg_`.

> **Out of scope:** Standard Sinhala transliteration, backend APIs, and performance / scalability / security testing.

---

## Singlish Input Types Covered

The 50 test cases span all 24 input types from Appendix 1:

| # | Input Type |
|---|---|
| 1 | Question forms |
| 2 | Command forms |
| 3 | Greetings |
| 4 | Requests |
| 5 | Responses |
| 6 | Repeated words |
| 7 | Inputs with punctuation marks |
| 8 | Romanization / spelling variants |
| 9 | Isolated English word insertions in Singlish |
| 10 | Multi-word English phrases in Singlish |
| 11 | English digital terms in Singlish |
| 12 | Platform / app names in Singlish |
| 13 | English abbreviations / acronyms in Singlish |
| 14 | English clipped forms in Singlish |
| 15 | Place names embedded in Singlish |
| 16 | Person names embedded in Singlish |
| 17 | Inputs with numbers and numeric suffixes |
| 18 | Inputs with currency |
| 19 | Inputs with time formats |
| 20 | Inputs with dates |
| 21 | Inputs with units of measurement |
| 22 | Inputs with slang and casual phrasing |
| 23 | Online identifiers in Singlish |
| 24 | Inputs containing emojis |

---

## Project Structure
## Project Structure

```
test_automation/IT23730724_requirments.txt
test_automation/IT23730724_Test cases.xlsx
test_automation/README.md
test_automation/test_automation.py
.gitattributes
.gitignore
README.md
```
---

## Prerequisites

- Python **3.11** or higher
- **Google Chrome** (recommended)
- pip (comes with Python)

---

## Setup Instructions

### 1. Clone the repository

```bash
git clone <repository-url>
cd ITPM_Assignment_1_IT23730724
```

### 2. Install Python dependencies

```bash
python -m pip install -U pip
python -m pip install playwright openpyxl
```

### 3. Install Playwright browsers

```bash
python -m playwright install
```

---

## Running the Tests

Run from the **project root** (the folder containing `test_automation/`):

```bash
python test_automation/test_automation.py \
  --excel "test_automation/IT23730724_Test cases.xlsx" \
  --url "https://www.pixelssuite.com/chat-translator" \
  --wait-ms 10000 \
  --type-delay-ms 80 \
  --slow-mo-ms 200 \
  --save-every 1 \
  --keep-open \
  --retries 15 \
  --retry-wait-ms 2000
```

Or if you are already inside the `test_automation/` folder:

```bash
python test_automation.py \
  --excel "IT23730724_Test cases.xlsx" \
  --url "https://www.pixelssuite.com/chat-translator" \
  --wait-ms 10000 \
  --type-delay-ms 80 \
  --slow-mo-ms 200 \
  --save-every 1 \
  --keep-open \
  --retries 15 \
  --retry-wait-ms 2000
```

A Chrome browser window will open and automatically execute each test case. Results are written to the Excel file after every row (`--save-every 1`).

### CLI Arguments Reference

| Argument | Default | Description |
|---|---|---|
| `--excel` | auto-detected | Path to the Excel test case file |
| `--url` | pixelssuite URL | Target application URL |
| `--wait-ms` | `5000` | Milliseconds to wait for translation output |
| `--type-delay-ms` | `30` | Delay between keystrokes (ms) |
| `--slow-mo-ms` | `0` | Playwright slow-motion delay (ms) |
| `--save-every` | `0` | Save Excel after every N rows (0 = end only) |
| `--retries` | `8` | Retry attempts when output is empty |
| `--retry-wait-ms` | `1000` | Wait between retries (ms) |
| `--keep-open` | off | Keep browser open after run completes |
| `--headless` | off | Run without a visible browser window |

---

## Checking Results

After the run completes, open `test_automation/IT23730724_Test cases.xlsx` and review the `Actual output` and `Status` columns.

| Status | Meaning |
|---|---|
| `PASS` | Actual output matches expected output exactly |
| `FAIL` | Actual output differs from expected output |
| `UI Error` | Browser interaction failed for that row |
| `COLLECTED` | Output captured but no expected value was set |

---

## Excel File Structure

The test case file follows the structure defined in Appendix 2 of the assignment brief:

| Column | Description |
|---|---|
| TC ID | Negative test case ID — all begin with `Neg_` (e.g. `Neg_0001`) |
| Input length type | `S` (≤ 30 chars) · `M` (31–299 chars) · `L` (300–450 chars) |
| Input | Singlish input text |
| Expected output | Correct Sinhala translation |
| Actual output | Output captured by Playwright (auto-filled) |
| Status | `PASS` / `FAIL` / `UI Error` (auto-filled) |
| Singlish input types covered | Input type(s) from Appendix 1 |
| Evidence or rationale | Justification for the input type classification |

