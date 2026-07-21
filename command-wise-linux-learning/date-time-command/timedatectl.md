# `timedatectl` Command – Control the System Time in Linux

The `timedatectl` command is used to query and change the system clock, timezone, and NTP settings.


**Show Current System Clock Settings**

```bash
timedatectl status
````

> **Output:** Displays the current time, timezone, NTP synchronization status, and RTC time.



**Show Machine-Readable Time Settings**

```bash
timedatectl show
```

> **Output:** Outputs the same information as `status`, but in a simplified machine-readable format.



**Set the System Clock Manually**

```bash
timedatectl set-time "2012-10-30 18:17:16"
```

> **Output:** Sets the system date and time.
**Note:** Requires root privileges.



**Enable or Disable NTP (Network Time Protocol)**

- Enable NTP synchronization:

  ```bash
  timedatectl set-ntp true
  ```

- Disable NTP synchronization:

  ```bash
  timedatectl set-ntp false
  ```


**List All Available Timezones**

```bash
timedatectl list-timezones
```

> **Output:** Prints all supported timezones, one per line.


**Set the System Timezone**

```bash
timedatectl set-timezone Asia/Dhaka
```

> **Output:** Sets the system timezone to **Asia/Dhaka**.


