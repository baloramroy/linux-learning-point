# `hostnamectl` – Hostname and System Identity Management

The `hostnamectl` command is used to manage hostnames and related system identity information on Linux systems using `systemd`.

---

## Display Current Hostname and System Information

**Show full hostname details:**
```bash
hostnamectl
````

**or**

```bash
hostnamectl status
```

**Displays:**

* Static, Pretty, and Transient hostnames
* Machine ID
* Boot ID
* Operating System
* Kernel version

---

## View Specific Hostname Types

- **Show the static hostname:**
  
  ```bash
  hostnamectl --static
  ```

- **Show the pretty hostname:**
  
  ```bash
  hostnamectl --pretty
  ```

- **Show the transient hostname:**
  
  ```bash
  hostnamectl --transient
  ```

---

## Set Hostnames

Linux supports **three types** of hostnames:

1. **Set Static Hostname**

    ```bash
    sudo hostnamectl set-hostname server1.example.com
    ```
  
    **or**
    
    ```bash
    sudo hostnamectl set-hostname server1.example.com --static
    ```

    > **Note:** Stored in the /etc/hostname file. It persists across reboots.

2. **Set Pretty Hostname**

    ```bash
    sudo hostnamectl set-hostname "Payment Gateway Node 1" --pretty
    ```
    
    > **Note:** A user-friendly, descriptive hostname.

3. **Set Transient Hostname**

    ```bash
    sudo hostnamectl set-hostname temp-server --transient
    ```
  
    > **Note:** Set temporarily for the current session. Does not survive a reboot.

- **Set all hostname types together:**

  ```bash
  sudo hostnamectl set-hostname server1.example.com --static --transient --pretty
  ```

---

## Remove a Hostname (Reset)

- **Reset all hostname types:**

  ```bash
  sudo hostnamectl set-hostname ""
  ```

- **Reset a specific hostname type:**

  Clear pretty hostname:
  
  ```bash
  sudo hostnamectl set-hostname "" --pretty
  ```
  
  Clear transient hostname:
  
  ```bash
  sudo hostnamectl set-hostname "" --transient
  ```

---

## Change the Chassis Type

- **Set the hardware chassis type (desktop, laptop, server, etc.):**

  ```bash
  sudo hostnamectl set-chassis laptop
  ```

- **Display the hardware chassis type**

  ```bash
  sudo hostnamectl chassis
  ```
  > **Output:** laptop

---

## Change the Deployment Environment

**Syntax:**

```bash
sudo hostnamectl set-deployment <environment>
```

**Example:**

- **Common environments:**
  * development
  * production
  * test

- **Set Environment type**
  
  ```bash
  sudo hostnamectl set-deployment production
  ```
  
- **Display Environment type**

  ```bash
  sudo hostnamectl deployment 
  ```
  > **Output:** production
  
---

## Set the Machine’s Location

**Syntax:**

  ```bash
  sudo hostnamectl set-location "<location>"
  ```

**Example:**

- Set Machine's Location
  
  ```bash
  sudo hostnamectl set-location "Datacenter Rack A1"
  ```
  > Sets the physical or logical machine location.

- Display Machine's Location

  ```bash
  sudo hostnamectl location
  ```
  > **Display:** Datacenter Rack A1

---

