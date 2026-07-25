#!/bin/bash
# organizer.sh
# Archives grades.csv with a timestamp, resets it with a fresh header, and logs the run.
 
ARCHIVE_DIR="archive"
CSV_FILE="${1:-grades.csv}"    # optional filename arg, defaults to grades.csv
LOG_FILE="organizer.log"
CSV_HEADER="assignment,group,score,weight"
 
# Create archive dir if missing
if [ ! -d "$ARCHIVE_DIR" ]; then
    mkdir "$ARCHIVE_DIR"
    echo "Created archive directory: $ARCHIVE_DIR"
fi
 
# Confirm the CSV exists
if [ ! -f "$CSV_FILE" ]; then
    echo "Error: '$CSV_FILE' not found in the current directory. Nothing to archive."
    exit 1
fi
 
# Skip if there's no actual grade data (empty or header-only)
LINE_COUNT=$(wc -l < "$CSV_FILE")
if [ "$LINE_COUNT" -le 1 ]; then
    echo "'$CSV_FILE' has no grade data to archive (only a header or empty). Skipping."
    exit 0
fi
 
# Timestamp + archive
TIMESTAMP=$(date +"%Y%m%d-%H%M%S")
NEW_NAME="grades_${TIMESTAMP}.csv"
mv "$CSV_FILE" "$ARCHIVE_DIR/$NEW_NAME"
 
# Reset with header row so grade-evaluator.py works right away
echo "$CSV_HEADER" > "$CSV_FILE"
 
# Log the run
echo "${TIMESTAMP} | Original: ${CSV_FILE} | Archived as: ${ARCHIVE_DIR}/${NEW_NAME}" >> "$LOG_FILE"
echo "Archived '${CSV_FILE}' as '${ARCHIVE_DIR}/${NEW_NAME}'."
echo "A new '${CSV_FILE}' (header only) has been created for the next batch of grades."
echo "Logged operation to ${LOG_FILE}."
