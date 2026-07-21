# `file` - Determine the type of a file

**Description:**

The `file` command is used to determine the type of a file based on its content rather than its extension. It is widely used in system administration, scripting, and debugging.

### Options

- `-b` → Do not prepend filenames to output (brief output).  
- `-i` → Output MIME type instead of a human-readable description.  
- `-L` → Follow symbolic links.  
- `-s` → Read block or character special files.  
- `-f filename` → Read filenames from a file instead of command line arguments.  
- `-z` – Look inside compressed files

---

### Examples

- List file type of a single file  
 
  ```bash
  file myscript.sh
  ````
  
  **Output:**
  ```text
  myscript.sh: Bourne-Again shell script, ASCII text executable
  ```
* Display file type without the filename (brief mode)

  ```bash
  file -b myscript.sh
  ```
  
  **Output:**
  ```text
  Bourne-Again shell script, ASCII text executable
  ```
  
* Show MIME type of a file

  ```bash
  file -i image.png
  ```
  
  **Output:**
  ```text
  image.png: image/png; charset=binary
  ```
  
* Determine type of all files in a directory

  ```bash
  file *
  ```
  
  **Output:**
  ```text
  script1.sh: ASCII text
  image1.jpg: JPEG image data, JFIF standard 1.01
  ```
* Follow symbolic links to determine the type of the target file

  ```bash
  file -L symlink_to_file
  ```
  
  **Output:**
  ```text
  symlink_to_file: ASCII text
  ```
  >**Purpose:** Check type of the actual file pointed to by symlink

* Read file names from another file and display types

  ```bash
  echo "file1.txt" > list.txt
  echo "image1.jpg" >> list.txt
  file -f list.txt
  ```
  
  **Output:**
  ```text
  file1.txt: ASCII text
  image1.jpg: JPEG image data, JFIF standard 1.01
  ```
  
  >**Purpose:** Batch check file types from a list

* Inspect special files (like device files)

  ```bash
  file -s /dev/sda
  ```
  
  >**Output:** /dev/sda: block special (disk)

- Look inside compressed files

  ```bash
  file -z archive.tar.gz
  ```
  >**Output:** Identifies contents of compressed file

---

## Real-Life Examples

* Check type of a log file in `/var/log`

  ```bash
  file /var/log/messages
  ```
  
  >**Output:** /var/log/messages: ASCII text

* Check type of a compressed zip archive

  ```bash
  file backup-2025-12-01.zip
  ```
  
  >**Output:** backup-2025-12-01.zip: Zip archive data, at least v2.0 to extract
  >
  >**Purpose:** Verify that a downloaded or transferred file is a valid zip archive

* Check type of an ISO image
  
  ```bash
  file CentOS-9.iso
  ```
  
  >**Output:** CentOS-9.iso: ISO 9660 CD-ROM filesystem data
  >
  >**Purpose:** Confirm ISO image before mounting or burning

* Check type of a symbolic link to a script

  ```bash
  file -L /usr/local/bin/myscript
  ```
  
  >**Output:** /usr/local/bin/myscript: Bourne-Again shell script, ASCII text executable
  >
  >**Purpose:** Check the actual file type even when using symlinks

---
