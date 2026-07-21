# `head` - Output the first part of files

**Description:**

Displays the first lines (default: 10) of one or more files or piped input.

**Options:**
  * `-n <number>` - Output the first `<number>` lines (or use a negative number to show all but the last `<number>` lines)
  * `-c <bytes>` - Output the first `<bytes>` bytes of the file
  * `-v` - Always print the file name header (verbose mode)

## Example of the `head` command

- Show the **first 10 lines** of a log file (default behavior)
  ```bash
  head /var/log/messages
  ```
  **Output:** First 10 lines of the log file.

- Show a **specific number of lines** from a file
  ```bash
  head -n 5 /etc/passwd
  ```
  **Output:** Shows the first 5 lines from `/etc/passwd`.

- Show lines until a specific **byte size**
  ```bash
  head -c 50 /etc/hosts
  ```
  **Output:** Shows only the first 50 bytes of the file.
  
  **Purpose:** Useful for checking file headers or metadata in binary or text files by size, not by line count.

- Show the first lines of **multiple files**
  ```bash
  head -n 3 file1.txt file2.txt
  ```
  **Output:** Displays the first 3 lines of each specified file, with a header separating them.

- Display everything **except the last N lines**
  ```bash
  head -n -20 mylog.log
  ```
  **Output:** Shows the entire file except the last 20 lines.
  
  **Purpose:** Useful when logs grow continuously and you need to ignore the most recent, often repetitive, tail end.

- Use the **verbose** option to print the file name header
  ```bash
  head -v /var/log/messages
  ```
  **Output:**
  ```
  ==> /var/log/messages <==
  line1
  ...
  ```
  **Purpose:** Makes the output clearer, especially in scripts or when processing multiple files, by explicitly showing which file the data comes from.

- Use `head` with a **pipeline**
  ```bash
  ps aux | head
  ```
  **Output:** First 10 rows of `ps aux`.

- Combine `head` with `grep` (**search + preview**)
  ```bash
  grep -i error /var/log/messages | head -n 10
  ```
  **Output:** First 10 matches of "error".


- Display `head` output with **line numbers**
  ```bash
  head /etc/passwd | nl
  ```
  **Output:** Top 10 lines with line numbers.
