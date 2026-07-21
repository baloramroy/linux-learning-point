# `cat` Command

**Description:**

`cat` (concatenate) is used to display **file contents**, create files, combine files, and redirect output. It is one of the most commonly used commands in Linux for quick file viewing.

### Options

- `-n` → Number all output lines  
- `-b` → Number only non-empty lines  
- `-s` → Squeeze repeated empty lines (show only one)  
- `-A` → Show all invisible characters (equivalent to -vET)  
- `-T` → Show TAB characters as ^I  
- `-E` → Show end of line with $  

## Basic Usage

- **Display a file's content**
  ```bash
  cat /etc/hosts
  ```
  Output: shows the full content of /etc/hosts  

- **Display multiple files**
  
  ```bash
  cat file1.txt file2.txt`
  ```
  >**Output:** prints file1 content followed by file2    

## Numbering Lines

- Show line numbers for every line (-n)
  ```bash
  cat -n /etc/passwd
  ```
  >**Output:** each line is prefixed with a number  

- Show line numbers only for non-empty lines (-b)
  ```bash
  cat -b script.sh
  ```
  >**Output:** only non-empty lines numbered  

## Formatting Output

- Remove repeated empty lines `(-s)`
  ```bash
  cat -s notes.txt
  ```
  >**Output:** multiple blank lines become a single blank line

- Show all invisible characters `(-A)`
  ```bash
  cat -A config.txt
  ```
  **Output:**
  - Tabs displayed as ^I
  - End of line as $
  - Non-printable chars shown
  
  >**Purpose:** Debug formatting issues, YAML indent issues, etc.

- Show end of lines only (-E)
  ```bash
  cat -E data.txt
  ```
  >**Output:** each line ends with `$`  
  >**Purpose:** Detect trailing spaces or blank lines.

- Show TAB characters `(-T)`
  ```bash
  cat -T Makefile
  ```
  >**Output:** tabs show as `^I`  
  >**Purpose:** Detect tabs vs spaces — critical for Makefiles.

## File Creation Using cat (Real-Life Use)

- Create a new file
  ```bash
  cat > message.txt
  Hello World
  This is a test file.
  <Ctrl + D>
  ```
  >**Purpose:** Quickly write small files without opening editors.

- Append text to a file
  ```bash
  cat >> log.txt
  New log entry added.
  <Ctrl + D>
  ```
  >**Output:** new text added to the end of log.txt  
  >**Purpose:** Update notes/logs without replacing file.

## Combining Files

- Merge multiple files into one
  ```bash
  cat part1.txt part2.txt > full.txt
  ```
  >**Output:** full.txt contains merged content  
  >**Purpose:** Useful for joining config fragments or logs.

- Append one file to another
  ```bash
  cat extra.txt >> main.txt
  ```
  >**Output:** content of extra.txt added to bottom of main.txt  

## View Logs with Cat (Real Production Use)

- View log with line numbers
  ```bash
  cat -n /var/log/messages
  ```
  >**Output:** all log lines numbered  

- View log and detect formatting issues
  ```bash
  cat -A /var/log/nginx/access.log
  ```
  >**Output:** invisible characters shown  
  >**Purpose:** Troubleshoot corrupted or malformed logs.

## Real-Life Examples (Practical Scenarios)

- Check YAML indentation issues
  ```bash
  cat -T -n playbook.yml
  ```
  >**Output:** shows ^I for tabs  
  >**Purpose:** Detect accidental TABs that break Ansible/YAML.

- Find extra blank lines in shell scripts
  ```bash
  cat -s -E script.sh
  ```
  >**Output:** compressed blank lines + $ marking EOL  
