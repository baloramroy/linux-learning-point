# tree – Display Directory Structure in Tree Format

**Desciption:**

`tree` – A command-line tool that recursively lists directories and files in a tree-like format, showing the hierarchical structure of a filesystem.

### Options:

- `-a` - Show all files including hidden files (dotfiles like .git, .env, .config)

- `-d` - List directories only, hide files

- `-f` - Print the full path prefix for each file

- `-L <level>` - Limit the display to a specific depth (replace <level> with a number)

- `-P <pattern>` - List only files that match the wildcard pattern (e.g., "*.conf")

- `-h` - Show file sizes in human-readable format (KB, MB, etc.)

- `-D` - Show last modification date of each file

- `-u` - Display the file owner (user)

- `-g` - Display the file group ownership

- `-p` - Show file permissions

---

- **Show complete directory structure**
  ```bash
  tree
  ````
  
  >**Purpose:**
  Displays files and folders in a tree-like hierarchical structure

- **Show tree of a specific directory**
  
  ```bash
  tree /var/log
  ```
  
  >**Purpose:**
  View directory structure of any specific location
  
- **Show hidden files and folders**
  
  ```bash
  tree -a
  ```
  
  >**Purpose:**
  Shows everything including dotfiles (.git, .env, .config)
  
- **Show only directories**
  
  ```bash
  tree -d /opt
  ```
  
  >**Purpose:**
  Hides files, shows only folders
  
- **Show full path for every file**
  
  ```bash
  tree -f /etc
  ```
  
  >**Purpose:**
  Displays absolute paths of that target directory
  
- **Limit the depth of directory display**
  
  ```bash
  tree -L 2 /usr
  ```
  
  >**Purpose:**
  Display only the first 2 levels
  
- **Show only files matching a pattern**
  
  ```bash
  tree -P "*.conf" /etc
  ```
  
  >**Purpose:**
  Filters and shows only specific files
  
- **Show file sizes in human-readable format**
  
  ```bash
  tree -h /var
  ```
  
  >**Purpose:**
  Shows file sizes (KB, MB, etc.)
  
- **Show last modification dates**
  
  ```bash
  tree -D /etc
  ```
  
  > **Purpose:**
  Displays modification date next to each file
  
- **Show user and group info**
  
  ```bash
  tree -u /var/www
  tree -g /var/www
  ```
  
  >**Purpose:**
  Shows file ownership
  
- **Show file permissions**
  
  ```bash
  tree -p /srv
  ```
  
  >**Purpose:**
  Displays permissions for all files/folders
  
- **Export tree output to a file**
  
  ```bash
  tree -L 2 /etc > etc-structure.txt
  ```
  
  >**Purpose:**
  Save output for documentation or reports

---
