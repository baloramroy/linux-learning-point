# `tail` - Display the Last Part of Files

**Description:**

The `tail` command displays the last lines of a file. It is mainly used for **log monitoring**, **debugging**, and **real-time tracking** of events in running systems.

**Options:**
  * `-n` - Show a specific number of lines from the end of the file
  * `-f` - Follow the file in real-time as it grows
  * `-F` - Similar to `-f`, but reopens the file if it's rotated (useful for logs)
  * `-c` - Display the last N bytes instead of lines
  * `--pid` - Stop following when the specified PID exits
  * `-q` - Suppress file names when tailing multiple files
  * `-v` - Always show file names when tailing multiple files

## Examples of the `tail` command

- View last 20 lines of a log file
  ```bash
  tail -n 20 /var/log/messages
  ```
  **Output:** Shows the last 20 lines of `/var/log/messages`.
  
  **Purpose:** Used when checking recent system log activity or troubleshooting errors.

- Monitor system logs as they update
  ```bash
  tail -f /var/log/secure
  ```
  **Output:** Displays new log entries live as they are added.
  
  **Purpose:** Very useful for monitoring authentication logs, debugging SSH issues, or watching events as they happen.

- Keep watching a log file that may rotate (e.g., nginx, apache)
  ```bash
  tail -F /var/log/nginx/access.log
  ```
  **Output:** Continues showing new lines even after log rotate or file recreation.
  
  **Purpose:** Used heavily in production servers because logs rotate regularly.

- Show last 100 bytes of a file
  ```bash
  tail -c 100 /var/log/messages
  ```
  **Output:** Shows exact 100 bytes from file end.
  
  **Purpose:** Useful when working with binary files, dumps, or checking file footers.

- Follow logs only until a process (e.g., PID 1234) stops running
  ```bash
  tail -f /var/log/secure --pid=1234
  ```
  **Output:** Shows live updates until PID 1234 exits, then automatically stops.

- Display last 10 lines of multiple log files
  ```bash
  tail -v /var/log/messages /var/log/secure
  ```
  **Output:** Shows file names first, then last 10 lines.
  
  **Purpose:** Used when checking the latest entries from multiple logs at once.

- Suppress file headers
  ```bash
  tail -q /var/log/messages /var/log/secure
  ```
  **Output:** Shows the content without printing file names.
  
  **Purpose:** Useful when piping output into another program or for clean automation.
