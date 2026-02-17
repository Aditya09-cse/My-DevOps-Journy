# Day 20 – Bash Scripting Challenge  
## Log Analyzer and Report Generator

## 📌 Objective
Build a Bash script to analyze log files, detect errors, extract critical events, and generate a summary report automatically.

---

## 🛠 Script: log_analyzer.sh

```bash
#!/bin/bash

# ===============================
# Log Analyzer and Report Generator
# ===============================

# -------- Task 1: Input Validation --------
if [ $# -eq 0 ]; then
    echo "❌ Error: Please provide a log file path."
    echo "Usage: ./log_analyzer.sh <logfile>"
    exit 1
fi

LOG_FILE="$1"

if [ ! -f "$LOG_FILE" ]; then
    echo "❌ Error: File '$LOG_FILE' does not exist."
    exit 1
fi

# -------- Setup Variables --------
DATE=$(date +%Y-%m-%d)
REPORT_FILE="log_report_${DATE}.txt"
TOTAL_LINES=$(wc -l < "$LOG_FILE")

# -------- Task 2: Error Count --------
ERROR_COUNT=$(grep -Ei "ERROR|Failed" "$LOG_FILE" | wc -l)
echo "Total Errors (ERROR/Failed): $ERROR_COUNT"

# -------- Task 3: Critical Events --------
CRITICAL_EVENTS=$(grep -n "CRITICAL" "$LOG_FILE")

echo ""
echo "--- Critical Events ---"
if [ -z "$CRITICAL_EVENTS" ]; then
    echo "No critical events found."
else
    echo "$CRITICAL_EVENTS"
fi

# -------- Task 4: Top 5 ERROR Messages --------
TOP_ERRORS=$(grep "ERROR" "$LOG_FILE" \
    | awk '{$1=$2=$3=""; print $0}' \
    | sed 's/^ *//' \
    | sort \
    | uniq -c \
    | sort -rn \
    | head -5)

echo ""
echo "--- Top 5 Error Messages ---"
echo "$TOP_ERRORS"

# -------- Task 5: Generate Summary Report --------
{
echo "=============================="
echo "       LOG ANALYSIS REPORT"
echo "=============================="
echo "Date of Analysis: $DATE"
echo "Log File: $LOG_FILE"
echo "Total Lines Processed: $TOTAL_LINES"
echo "Total ERROR/Failed Count: $ERROR_COUNT"
echo ""
echo "--- Top 5 Error Messages ---"
echo "$TOP_ERRORS"
echo ""
echo "--- Critical Events ---"

if [ -z "$CRITICAL_EVENTS" ]; then
    echo "No critical events found."
else
    echo "$CRITICAL_EVENTS"
fi

} > "$REPORT_FILE"

echo ""
echo "✅ Report generated: $REPORT_FILE"

# -------- Task 6: Archive Processed Logs --------
ARCHIVE_DIR="archive"
mkdir -p "$ARCHIVE_DIR"
mv "$LOG_FILE" "$ARCHIVE_DIR/"
echo "📦 Log file moved to $ARCHIVE_DIR/"
```
### Sample Output
  - Total Lines Processed: 2000
  - Total ERROR/Failed Count: 305
  - Top 5 repeated ZooKeeper errors extracted
  - Report generated as: log_report_2026-02-17.txt
  - Log file moved to archive/

### Commands Used
  - grep → Searching patterns
  - grep -n → Line numbers
  - wc -l → Counting lines
  - awk → Cleaning log prefixes
  - sort → Sorting output
  - uniq -c → Counting repeated messages
  - head -5 → Top 5 results
  - mkdir -p → Create directory safely
  - mv → Move processed log
### What I Learned
  - How to chain multiple Linux commands for real-world log processing
  - Importance of input validation in scripts
  - How automation saves time in production troubleshooting
### Key Takeaway
 Manual log checking is slow and error-prone.
 Automation makes troubleshooting faster and scalable.

 #90DaysOfDevOps
#DevOpsKaJosh
#TrainWithShubham
