
# ls – List files and directories

The `ls` command is used to **list** directory contents in Linux and Unix systems. It displays **files and directories** in the current working directory or specified location, showing information such as **names, permissions, sizes, and timestamps** depending on the **options** used.

**Options**

- `-a` – Show hidden files (including those starting with `.`)
- `-d` – List directories themselves, not their contents
- `-h` – Print sizes in human readable format (e.g., 1K, 234M, 2G)
- `-i` – Print the index number (inode) of each file
- `-l` – Use long listing format
- `-r` – Reverse order while sorting
- `-R` – List subdirectories recursively
- `-S` – Sort by file size, largest first
- `-t` – Sort by modification time, newest first
- `-X` – Sort alphabetically by extension

## Example with Various Options

- **Show hidden files**

  ```bash
  ls -a
  ```
  **Output:**
  ```
  .   ..   .bashrc   .config   documents   file.txt   pictures
  ```

- **List directories themselves, not their contents**
  ```bash
  ls -ld /home/broy/*
  ```
  **Output:**
  ```
  drwxr-xr-x 2 broy broy 4096 Jan 15 10:30 /home/broy/documents
  drwxr-xr-x 2 broy broy 4096 Jan 12 14:22 /home/broy/downloads
  drwxr-xr-x 2 broy broy 4096 Jan 10 09:15 /home/broy/pictures
  ```

- **Print size in human readable format**
  ```bash
  ls -lh
  ```
  **Output:**
  ```
  -rw-r--r-- 1 user user  15K Jan 15 10:30 report.pdf
  -rw-r--r-- 1 user user 2.3M Jan 14 16:45 image.jpg
  drwxr-xr-x 2 user user 4.0K Jan 13 11:20 documents
  ```

- **Print the index number of each file**
  ```bash
  ls -li
  ```
  **Output:**
  ```
  1234567 -rw-r--r-- 1 user user  1520 Jan 15 10:30 file1.txt
  1234568 drwxr-xr-x 2 user user  4096 Jan 14 16:45 folder1
  1234569 -rw-r--r-- 1 user user 23456 Jan 13 11:20 file2.txt
  ```

- **Long listing format**
  ```bash
  ls -ll
  ```
  **Output:**
  ```
  total 24
  -rw-r--r-- 1 user user  1520 Jan 15 10:30 file1.txt
  drwxr-xr-x 2 user user  4096 Jan 14 16:45 documents
  -rw-r--r-- 1 user user 23456 Jan 13 11:20 report.pdf
  ```

- **Reverse order while sorting**
  ```bash
  ls -lr
  ```
  **Output:**
  ```
  -rw-r--r-- 1 user user 23456 Jan 13 11:20 report.pdf
  drwxr-xr-x 2 user user  4096 Jan 14 16:45 documents
  -rw-r--r-- 1 user user  1520 Jan 15 10:30 File1.txt

  ```

- **List subdirectories recursively**
  ```bash
  ls -lR
  ```
  **Output:**
  ```
  total 12
  drwxr-xr-x 2 user user 4096 Jan 15 10:30 documents
  -rw-r--r-- 1 user user 1520 Jan 14 16:45 file.txt
  
  ./documents:
  total 8
  -rw-r--r-- 1 user user 800 Jan 13 11:20 doc1.pdf
  -rw-r--r-- 1 user user 650 Jan 12 09:30 doc2.txt
  ```

- **Sort by file size, largest first**
  ```bash
  ls -lS
  ```
  **Output:**
  ```
  -rw-r--r-- 1 user user 23456 Jan 13 11:20 large_file.zip
  -rw-r--r-- 1 user user  1520 Jan 15 10:30 medium_file.txt
  -rw-r--r-- 1 user user   256 Jan 14 16:45 small_file.conf
  ```

- **Sort by time, newest first**
  ```bash
  ls -lt
  ```
  **Output:**
  ```
  -rw-r--r-- 1 user user  1520 Jan 15 10:30 newest_file.txt
  -rw-r--r-- 1 user user   256 Jan 14 16:45 yesterday_file.conf
  -rw-r--r-- 1 user user 23456 Jan 13 11:20 older_file.zip
  ```

- **Sort alphabetically by extension**
  ```bash
  ls -lX
  ```
  **Output:**
  ```
  -rw-r--r-- 1 user user   256 Jan 14 16:45 config.conf
  -rw-r--r-- 1 user user  1520 Jan 15 10:30 document.txt
  -rw-r--r-- 1 user user 23456 Jan 13 11:20 archive.zip
  ```

- **Sort by file size, largest last in reverse order**
  ```bash
  ls -lSr
  ```
  **Output:**
  ```
  -rw-r--r-- 1 user user   256 Jan 14 16:45 small_file.conf
  -rw-r--r-- 1 user user  1520 Jan 15 10:30 medium_file.txt
  -rw-r--r-- 1 user user 23456 Jan 13 11:20 large_file.zip
  ```

- **Sort by time, newest last in reverse order**
  ```bash
  ls -ltr
  ```
  **Output:**
  ```
  -rw-r--r-- 1 user user 23456 Jan 13 11:20 older_file.zip
  -rw-r--r-- 1 user user   256 Jan 14 16:45 yesterday_file.conf
  -rw-r--r-- 1 user user  1520 Jan 15 10:30 newest_file.txt
  ```

