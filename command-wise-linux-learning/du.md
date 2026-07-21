# `du` - Disk Usage

**Description:**

The `du` (disk usage) command estimates file and directory **space** usage. It displays the amount of disk space **consumed**, helping identify **large** files or folders, commonly used for **storage analysis** and **cleanup**.

## Options:

* `-a` - Show sizes for all files, not just directories
* `-b` - Display in bytes (equivalent to --apparent-size --block-size=1)
* `-c` - Produce a grand total 
* `-h` - Human-readable format (KB, MB, GB)  
* `-s` - Display only a total for each argument (summarize)  
* `--exclude=PATTERN` - Exclude files that match PATTERN  
* `--apparent-size` - Print apparent sizes, not disk usage  
* `--max-depth=N` - Show total for a directory only if it is N or fewer levels below the command line argument    
* `--inodes` - Display inode usage instead of block usage

## Basic Usage

- Display disk usage of a directory
  ```bash
  du /path/to/directory
  ```
  **Output:** Shows disk usage in **kilobytes** for each subdirectory under the specified path.

- Display Disk Usage for All Subdirectories
  ```bash
  du -a /path/to/directory
  ```
  **Output:** Shows size of each file and directory **recursively**.

## Human-Readable Format

- Display disk usage in a human-readable format (KB, MB, GB)
  ```bash
  du -h /path/to/directory
  ```
  **Output:** 12K, 4.0M, 1.2G (depending on the size of subdirectories).

## Summarize Total Size

- Show only the total size of a directory
  ```bash
  du -sh /path/to/directory
  ```
  **Output:** 1.5G  
  **Purpose:** Quickly see total disk usage without listing subdirectories.

- Show only the current directory size
  ```bash
  du -sh .
  ```
  **Output:** 500M  
  **Purpose:** Fast check of space used by the current working directory.

- Check total disk usage of several directories at once
  ```bash
  du -sh /var /home /opt
  ```
  **Output:**  
  - **1.5G**    /var  
  - **3.2G**    /home  
  - **500M**    /opt  
  
  **Purpose:** Compare sizes across multiple directories.

- Exclude individual files, showing only directories
  ```bash
  du -sh */
  ```
  **Output:**  
  - **200M**    subdir1  
  - **150M**    subdir2  

  **Purpose:** Quickly summarize usage per top-level directory.

## Sort Output by Size | Summarize Largest Directories Only

- List subdirectories sorted by size (requires piping to sort)
  ```bash
  du -h /path/to/directory | sort -hr
  ```
  **Output:**  
  - **1.2G**    /path/to/directory/biggest_folder  
  - **800M**    /path/to/directory/other_folder  

  **Purpose:** Helps identify which directories are consuming the **most space**.

- Find top 5 largest directories
  ```bash
  du -ah /path/to/directory | sort -hr | head -n 5
  ```
  **Output:**  
  - **1.2G**    /path/to/directory/biggest_folder  
  - **900M**    /path/to/directory/second_folder  
  
  **Purpose:** Quickly find **storage hogs**.

## Display Only Grand Total (all nested)

- Get the total of a directory including all subdirectories
  ```bash
  du -ch /path/to/directory | grep total
  ```
  **Output:** 3.5G total  
  **Purpose:** Summarize disk usage including all nested directories.

- Summarize total size in human-readable format
  ```bash
  du -shc /path/to/directory1 /path/to/directory2
  ```
  **Output:**  
  - **2.0G**    /path/to/directory1  
  - **1.5G**    /path/to/directory2  
  - **3.5G**    total  
  
  **Purpose:** Summarize multiple directories with an **overall total**.

## Display Disk Usage of Recently Modified Files Only

- Show sizes of recently modified files
  ```bash
  find /path/to/directory -type f -mtime -7 -exec du -h {} +
  ```
  **Output:** Sizes of files modified in the **last 7 days**.  
  **Purpose:** Monitor recent changes affecting disk usage.

## Exclude Specific Files or Directories

- Ignore certain files or directories while calculating disk usage
  ```bash
  du -sh --exclude="*.log" /var/log
  ```
  **Output:** 1.2G  
  **Purpose:** Skip **temporary or irrelevant files**.

## Display Apparent Size (not disk blocks)

- Use actual file sizes, ignoring disk block allocation
  ```bash
  du --apparent-size -h /path/to/directory
  ```
  **Output:** Shows the **exact size** files occupy logically.  
  **Purpose:** Useful to check storage for **sparse files**.

## Show Disk Usage at Specific Depth

- Limit the output to a certain depth of subdirectories
  ```bash
  du -h --max-depth=1 /path/to/directory
  ```
  **Output:**  
  - **200M**    /path/to/directory/subdir1  
  - **150M**    /path/to/directory/subdir2  
  - **350M**    /path/to/directory  
  
  **Purpose:** Useful to see only **top-level subdirectories' usage**.

## Disk Usage in Blocks & Inodes

- Show usage in 512-byte blocks (default in some scripts)
  ```bash
  du -b /path/to/directory
  ```
  **Output:** **524288** /path/to/directory/file1  
  **Purpose:** Required for scripts that parse **block sizes**.

- Show number of inodes used (not bytes)
  ```bash
  du --inodes -a /path/to/directory
  ```
  **Output:** Number of files and directories (inodes) used.  
  **Purpose:** Detect **inode exhaustion** on servers with many small files.

