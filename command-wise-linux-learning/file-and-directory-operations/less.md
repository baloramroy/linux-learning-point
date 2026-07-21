# `less` - View file contents page by page

**Description:**

View large files one page at a time. Allows forward and backward navigation, searching, and live monitoring.

**Options:**
* `-N` - Show line numbers permanently
* `-R` or `-r` - Display raw control characters (preserve colors)
* `+F` - Start in **follow** mode (like `tail -f`)

## Examples of the `less` command

- View a large system file
  ```bash
  less /etc/passwd
  ```
  **Purpose:** Navigate long files without loading the entire file into memory.

- View log files with color support
  ```bash
  less -R /var/log/messages
  ```
  **Purpose:** Read logs that contain **color codes** or special formatting.

- Follow live logs while retaining scrollback ability
  ```bash
  less +F /var/log/secure
  ```
  **Purpose:** Monitor **live logs** (like `tail -f`) but still scroll back through previous content.

- View configuration files with permanent line numbers
  ```bash
  less -N /etc/httpd/conf/httpd.conf
  ```
  **Purpose:** Check or debug **config files** with precise line references.

## Navigation inside `less`

**Move Up/Down**
* Down: ↓ arrow, **j**, or **Space**
* Up: ↑ arrow or **k**
**Use case:** Navigate long log files easily.

**Search Inside File**
* Search forward: **/keyword**
* Search backward: **?keyword**
* After searching:
  * **n** → next match
  * **N** → previous match
  * **ESC** → quit search

**Go to Top/Bottom**
* Top: **g**
* Bottom: **G**  
**Use case:** Jump to the **latest logs** instantly.

**Jump by Page**
* Page down: **Space**
* Page up: **b**  
  **Use case:** Scroll fast through large files.

**Show Line Numbers**
* Press: **-N** (toggle)  
**Use case:** Useful when checking **config files**.

**Follow File Like `tail -f`**
* Press: **F**  
* This makes `less` work like: `tail -f file` or `less -F file`  
**Use case:** Monitoring live logs while still being able to scroll back.

**Jump to a Specific Line**
* **123g** → jump to line 123

**View Non-Printable Characters**
* `less -r` or `less -R` (common)  
**Output:** Useful for logs containing colors.

**Quit Less**
* Press: **q**
