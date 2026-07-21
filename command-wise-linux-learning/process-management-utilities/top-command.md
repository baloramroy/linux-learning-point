
# `top` – Real Time Process Monitoring

**Description:**

The **top** command in Linux is a **real-time monitoring** tool that provides a **dynamic view** of your system's **processes and resource usage**.

**Options:**
* `?` - Display help screen with all keyboard shortcuts.
* `q` - Quit top and return to the shell.
* `l` - Toggle load average line (1m/5m/15m).
* `t` - Toggle task summary line.
* `m` - Toggle memory and swap usage lines.
* `1` - Toggle between combined CPU line or per-core CPU lines.
* `s` - Change refresh rate (update interval in seconds).
* `b` - Enable/disable reverse highlighting for running processes.
* `B` - Enable bold headers and running processes.
* `H` - Toggle between process view and thread view.
* `u` or `U` - Filter processes by username.
* `M` - Sort processes by memory usage (descending).
* `P` - Sort processes by CPU usage (descending).
* `k` - Kill a process (prompts for PID and signal).
* `r` - Renice a process (change priority).
* `f` - Manage columns/fields (add/remove/reorder).
* `W` - Save current top configuration to `~/.toprc`.
* `E` (Shift+E) - Cycle memory units in summary area (KiB → MiB → GiB...).
* `e` - Cycle memory units in process list (KiB → MiB → GiB...).

## Help and General Settings

- **Help screen**
  
  ```
  ?
  ```
  
  **Output:**
  Displays a help window listing all available keyboard shortcuts.
  
  **Purpose:**
  To quickly view all commands inside top.

- **Quit top**

  ```
  q
  ```
  
  **Output:**
  Exits top and returns to the shell.
  
  **Purpose:**
  To leave the top interface.

## Toggles (Headers and CPU View)

- **Toggle load average line**
  
  ```
  l
  ```
  
  **Output:**
  Shows or hides the load average line (1m/5m/15m).
  
  **Purpose:**
  To reduce or expand displayed system information.

- **Toggle task summary line**

  ```
  t
  ```
  
  **Output:**
  Shows or hides the tasks summary line.
  
  **Purpose:**
  To simplify the screen or show more task details.

- **Toggle memory usage line**

  ```
  m
  ```
  
  **Output:**
  Shows or hides memory and swap usage lines.
  
  **Purpose:**
  To reduce clutter or focus on CPU/process info.

- **Toggle CPU single/per-core view**

  ```
  1
  ```
  
  **Output:**
  Switches between one combined CPU line or multiple per-CPU lines.
  
  **Purpose:**
  To monitor CPU usage per core when needed.

## View top in Human Readable value

- **Press `Shift + E` to cycle through memory display units**
  ```
  E
  ```
  **Output**
  This changes the units at the top of each column (affects multiple columns)

  **Note**
  Units cycle through: `KiB` → `MiB` → `GiB` → `TiB` → `PiB` → `EiB`

## Refresh and Display Settings

- **Change refresh rate**

  ```
  s
  ```
  
  **Output:**
  Prompts for a new refresh interval in seconds.
  
  **Purpose:**
  To change how frequently top updates.


## Highlighting Options

- **Enable/Disable Reverse Highlighting for Running Processes**
  
  ```
  b
  ```
  
  **Output:**
  Enables/disables reverse highlighting for running processes.
  
  **Purpose:**
  To easily spot active processes.
  
- **Enable Bold Headers and Running Processes**
  
  ```
  B
  ```
  
  **Output:**
  Headers and running processes appear in bold.
  

## Thread Management

- **Toggle Between Process and Thread View**
  
  ```
  H
  ```
  
  **Output:**
  Switches between process-only view and per-thread view.


## Filtering and Sorting

- **Filter Processes by User**

  ```
  u
  ```
  
  **or**
  
  ```
  U
  ```


  - **Prompts for a username:**
    Username to filter by: `broy`
  
    **Output:**
    Then shows only that user’s processes.

- **Sort by Memory Usage**
  
  ```
  M
  ```
  
  **Output:**
  Sorts processes by memory usage (descending).
  
- **Sort by CPU Usage**
  
  ```
  P
  ```
  
  **Output:**
  Sorts processes by CPU usage (descending).


## Process Management

- **Kill a process**
  
  ```
  k
  ```
  
  **Output:**
  Prompts for PID and optional signal.
  
- **Renice a process (Change Priority)**
  
  ```
  r
  ```
  
  **Output:**
  Prompts for PID and nice value.
  
  **Purpose:**
  To adjust process priority.


## Customization

- **Manage Columns (Fields)**
  
  ```
  f
  ```
  
  **Output:**
  Opens field management menu for adding/removing/reordering columns.

- **Save Current Top Configuration**

  ```
  W
  ```
  
  **Output:**
  Saves current settings to `~/.toprc`.

---

