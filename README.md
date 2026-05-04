# IT3040 – ITPM Assignment 1: Transliteration Accuracy Testing

Playwright-based automation for testing the Chat Sinhala transliteration function at [pixelssuite.com/chat-translator](https://www.pixelssuite.com/chat-translator).

## Prerequisites

- Python 3.11 or 3.12
- Google Chrome (recommended)

## Setup

```bash
pip install -U pip
pip install playwright openpyxl
playwright install
```

## Running the Tests

From the project root (where `test_automation/` folder is located):

```bash
python test_automation/test_automation.py --excel "test_automation/Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 5000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --keep-open
```

Or if running from inside the `test_automation/` folder:

```bash
python test_automation.py --excel "Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 5000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --keep-open
```

## Checking Results

After the run completes, open `test_automation/Assignment 1 - Test cases.xlsx`. The `Actual output` and `Status` columns will be filled automatically.

- **PASS** – actual output matches expected output exactly
- **FAIL** – actual output differs from expected output
- **UI Error** – browser interaction failed for that row

## Project Structure

```
test_automation/
├── test_automation.py          # Main Playwright automation script
├── Assignment 1 - Test cases.xlsx  # Test cases with results
populate_excel.js               # (Dev utility) Node.js script used to populate Excel
README.md                       # This file
```
