# `grep` - Search for Pattern in File

## Description:
The grep command in Linux is a powerful tool used to search for text patterns within files. The name grep stands for Global Regular Expression Print.

**Options:**
  * `-c` – Count the number of matches
  * `-i` – Case-insensitive search
  * `-l` – Display filenames only
  * `-m` – Limit the number of matches
  * `-n` – Display line numbers
  * `-r` – Search recursively in directories
  * `-v` – Invert the match
  * `-w` – Match whole words
  * `--color` – Highlight matches

---

## Basic & Most Common grep Commands

- Search for a pattern in a file
  ```bash
  grep "pattern" file.txt
  ```
  **Output:** Lines containing the pattern

- Case-insensitive search
  ```bash
  grep -i "pattern" file.txt
  ```
  **Output:** Matches ignoring uppercase/lowercase

- Exclude matching lines
  ```bash
  grep -v "pattern" file.txt
  ```
  **Output:** Lines NOT matching the pattern\
  **Purpose:** Filter unwanted entries (very useful in logs).

- Count matching lines
  ```bash
  grep -c "pattern" file.txt
  ```
  **Output:** Number of matched lines\
  **Purpose:** Count how many times a pattern appears.

- Match whole words only
  ```bash
  grep -w "pattern" file.txt
  ```
  **Output:** Only whole word matches\
  **Purpose:** Avoid partial matches like “car” matching “scary”.

- Search using patterns from a file
  ```bash
  grep -f patterns.txt file.txt
  ```
  **Output:** Matches any pattern listed in file\
  **Purpose:** Bulk multi-pattern searching.

---

## Search Across Files & Directories

- Search recursively inside directories
  ```bash
  grep -r "pattern" /var/log/
  ```
  **Output:** Matches from files inside directories\
  **Purpose:** Search logs/configs deeply.

- Search recursively including symlinks
  ```bash
  grep -R "pattern" /etc/
  ```
  **Output:** Recursive search with symlink follow\
  **Purpose:** Explore config folders completely.

- Show only filenames that contain the pattern
  ```bash
  grep -l "pattern" *.log
  ```
  **Output:** File names with matches\
  **Purpose:** Quickly identify files with certain content.

- Show filenames that do NOT contain the pattern
  ```bash
  grep -L "pattern" *.log
  ```
  **Output:** File names without matches\
  **Purpose:** Find missing configs or mismatched settings.

---

## Output Formatting & Context Control

- Show matching lines with line numbers
  ```bash
  grep -n "pattern" file.txt
  ```
  **Output:** Each matching line is **prefixed** with its corresponding **line number** from the file (e.g., `15:This line contains the pattern`).\
  **Purpose:** Locate exact lines.

- Always include the filename in the output, even with a single file
  ```bash
  grep -H "pattern" *.conf
  ```
  **Output:** Each match is shown with the format `filename: matching line` (e.g., `nginx.conf:server_name example.com;`).\
  **Purpose:** Essential when searching multiple files or piping results to other commands.

- Extract only the matching portion of text, not the entire line
  ```bash
  grep -o "pattern" file.txt
  ```
  **Output:** Only the matched portion\
  **Purpose:** Extract values from logs/files.

- Show match + 3 lines after it
  ```bash
  grep -A 3 "pattern" file.txt
  ```
  **Output:** Match + after-context\
  **Purpose:** View follow-up logs after an event.

- Show match + 3 lines before
  ```bash
  grep -B 3 "pattern" file.txt
  ```
  **Output:** Match + before-context\
  **Purpose:** Inspect what led to an issue.

- Show match + 3 lines before & after
  ```bash
  grep -C 3 "pattern" file.txt
  ```
  **Output:** Match + surrounding context\
  **Purpose:** Understand full log context.

---

## Using Regular Expressions

- Search for lines starting with "Hello":
  ```bash
  grep "^Hello" example.txt
  ```

- Search for lines ending with "grep":
  ```bash
  grep "grep$" example.txt
  ```

- Search for lines containing either "Linux" or "World":
  ```bash
  grep "Linux\|World" example.txt
  ```

---

## Performance & Script-Oriented Usage

- Highlight matches in output
  ```bash
  grep --color=auto "pattern" file.txt
  ```
  **Output:** Color-highlighted matches\
  **Purpose:** Easier visual search in terminals.

- Stop searching after first 5 matches
  ```bash
  grep -m 5 "pattern" large.log
  ```
  **Output:** First five matches\
  **Purpose:** Faster search in huge logs.

- Quiet mode (no output, exit code only)
  ```bash
  grep -q "pattern" file.txt
  ```
  **Output:** No output\
  **Purpose:** Used in if-statements in scripts.

---

## Combining grep With Other Tools

- Search processes for a service
  ```bash
  ps aux | grep nginx
  ```
  **Output:** Process lines containing nginx\
  **Purpose:** Check if a service is running.

- Search systemd journal for failures
  ```bash
  journalctl -u sshd | grep "Failed"
  ```
  **Output:** SSH failed attempts\
  **Purpose:** Security & login analysis.

- Filter kernel messages for errors
  ```bash
  dmesg | grep -i error
  ```
  **Output:** Error messages from kernel\
  **Purpose:** Hardware & kernel debugging.

- Search logs for errors/warnings
  ```bash
  cat /var/log/messages | grep -E "warn|error|fail"
  ```
  **Output:** Warning/error/failure lines\
  **Purpose:** Log investigation.

- Check which service is listening on port 80
  ```bash
  ss -tulpn | grep 80
  ```
  **Output:** Port 80 process details\
  **Purpose:** Web server troubleshooting.

---

## Search Multiple Words with grep

- Search multiple words (OR condition)
  ```bash
  grep -E "error|failed|critical" /var/log/messages
  ```

- Case-insensitive Search
  ```bash
  grep -Ei "failed|timeout" /var/log/messages
  ```

- Highlight Matches with color
  ```bash
  grep --color=auto -E "error|critical" file.txt
  ```

- Count Matches
  ```bash
  grep -E -c "error|failed" file.log
  ```

- Print Line Numbers
  ```bash
  grep -E -n "error|failed" file.log
  ```

- Search multiple words (AND condition)
  ```bash
  grep -E "error" app.log | grep -E "database"
  ```
  **Output:** Find lines containing both error AND database

---

## Search Multiple Words from cat Output

- Option A (OR condition)
  ```bash
  cat /etc/passwd | grep -E "231012|210459|241132|210639|231006"
  ```

- Option B (AND condition)
  ```bash
  cat filename | grep -E "word1" | grep -E "word2"
  ```

---

## Grep use in real life environment

- Filtering lines from 22:07 to 22:12 that contain ERROR.
  ```bash
  grep -E '2025-12-16 22:0[7-9]|2025-12-16 22:1[0-2]' output.log | grep 'ERROR'
  ```

- Summarize the actual failures rather than all [ERROR] logs
  ```bash
  grep -E '2025-12-16 22:0[7-9]|2025-12-16 22:1[0-2]' output.log | grep 'ERROR' | grep -v 'EXECUTED_SUCCESS'
  ```

---