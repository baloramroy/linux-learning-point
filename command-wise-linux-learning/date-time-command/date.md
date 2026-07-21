# 🕒`date` Command – Displaying Date and Time in Linux

## Display Current Date and Time

- Run to show the system’s current date and time:

  ```bash
  date
  ````

  > **Output:** Mon Nov 17 02:38:37 PM +06 2025
  
- Run to show the Universal Time (UTC)

  ```bash
  date -u
  ```
  > **Output:** Mon Nov 17 08:38:18 AM UTC 2025



## Display Relative Dates

- **Yesterday:**

  ```bash
  date -d "yesterday"
  ```
  > **Output:** Sun Nov 16 04:12:33 PM +06 2025

- **Tomorrow:**

  ```bash
  date -d "tomorrow"
  ```
  > **Output:** Tue Nov 18 04:12:58 PM +06 2025

- **5 days ago:**

  ```bash
  date -d "-5 days"
  ```
  > **Output:** Wed Nov 12 04:13:24 PM +06 2025

- **10 days later:**

  ```bash
  date -d "+10 days"
  ```
  > **Output:** Thu Nov 27 04:13:54 PM +06 2025



## Display Date in a Custom Format

You can format the output using the `+` sign followed by format specifiers.

**Common Format Specifiers**

| Specifier | Meaning               |
| --------- | --------------------- |
| `%Y`      | Year (e.g., 2025)     |
| `%m`      | Month (01–12)         |
| `%d`      | Day (01–31)           |
| `%H`      | Hour (24-hour format) |
| `%I`      | Hour (12-hour format) |
| `%M`      | Minutes               |
| `%S`      | Seconds               |
| `%p`      | AM/PM                 |
| `%A`      | Full weekday (Monday) |
| `%B`      | Full month (February) |


### Examples

**Display date in YYYY-MM-DD format:**

```bash
date +"%Y-%m-%d"
```

> **Output:** 2025-02-25


**Display date & time in DD/MM/YYYY HH:MM:SS:**

```bash
date +"%d/%m/%Y %H:%M:%S"
```
> **Output:** 25/02/2025 10:45:23


**Display only day and month:**

```bash
date +"%A, %B %d"
```
> **Output:** Monday, February 25

**Show time in HH:MM format:**

```bash
date +%R
```

> **Output:** 20:33


**Show date in MM/DD/YYYY format:**

```bash
date +%x
```

> **Output:** 02/27/2022


---

## Set System Date and Time (Requires root)

**Syntax**

```bash
sudo date MMDDhhmm[[CC]YY][.ss]
```

**Breakdown:**

* **MM** → Month
* **DD** → Day
* **hh** → Hour
* **mm** → Minutes
* **[CC]YY** → Year (optional)
* **ss** → Seconds (optional)

**Example**

- Set date to **February 25, 2025, 14:30:00**:

  ```bash
  sudo date 022514302025.00
  ```

  > ⚠️ **Note: Normally, Linux syncs time automatically using NTP.**



## Unix Timestamp Conversions

- **Convert a date to Unix timestamp:**

  ```bash
  date -d "2025-02-25 14:30:00" +%s
  ```
  
  > **Output:** 1740445800


- **Convert Unix timestamp to human-readable:**

  ```bash
  date -d @1740445800
  ```
  
  > **Output:** Tue Feb 25 14:30:00 UTC 2025



## Get the Running Week Number

```bash
date +"%U"
```

> **Output:** 08



## Get Timezone Information

```bash
date +"%Z %z"
```

> **Output:** UTC +06 +0600

## Practical Example

**Automate Date Logging in Scripts**

  Useful when adding timestamps to log files:
  
  ```bash
  echo "Backup completed at $(date +"%Y-%m-%d %H:%M:%S")" >> backup.log
  ```

