| Command                             | Description                                            | Example                              | Output Example                  |
| ----------------------------------- | ------------------------------------------------------ | ------------------------------------ | ------------------------------- |
| **`date`**                          | Display the current system date and time.              | `date`                               | `Mon Oct 20 19:45:00 EEST 2025` |
| **`date +"%d-%m-%Y"`**              | Show only the date in a custom format.                 | `date +"%d-%m-%Y"`                   | `20-10-2025`                    |
| **`date +"%H:%M:%S"`**              | Show only the time in 24-hour format.                  | `date +"%H:%M:%S"`                   | `19:45:00`                      |
| **`date -s "2025-10-20 19:30:00"`** | Set the system date and time (requires root).          | `sudo date -s "2025-10-20 19:30:00"` | —                               |
| **`date +%s`**                      | Display the Unix timestamp (seconds since 1970-01-01). | `date +%s`                           | `1760985900`                    |
| **`date -d @<timestamp>`**          | Convert Unix timestamp to human-readable format.       | `date -d @1760985900`                | `Mon Oct 20 19:45:00 EEST 2025` |
| **`cal`**                           | Show the current month’s calendar.                     | `cal`                                | Displays current month calendar |
| **`cal YEAR`**                      | Show the full calendar for a given year.               | `cal 2025`                           | Displays all months of 2025     |
| **`cal MONTH YEAR`**                | Show a specific month of a specific year.              | `cal 10 2025`                        | Displays October 2025 calendar  |
