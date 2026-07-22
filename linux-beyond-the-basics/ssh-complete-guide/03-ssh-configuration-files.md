# SSH Configuration Files

## Introduction

OpenSSH uses configuration files to define how SSH clients initiate connections and how SSH servers accept and manage incoming connections.

There are two primary configuration files:

* **Client Configuration File** – Controls the behavior of the SSH client.
* **Server Configuration File** – Controls the behavior of the SSH server (`sshd`).

Understanding these configuration files is essential for system administrators because nearly every aspect of SSH—authentication, ports, security policies, forwarding, logging, and access control—is configured through them.

This article introduces the SSH configuration files, their locations, syntax, and how configuration changes are applied. Detailed explanations of individual configuration directives will be covered in later articles.

---

## SSH Configuration Overview

OpenSSH separates configuration into two categories:

| Configuration Type   | Purpose                                                    | Typical User              |
| -------------------- | ---------------------------------------------------------- | ------------------------- |
| Client Configuration | Defines how SSH clients connect to remote systems          | End users, administrators |
| Server Configuration | Defines how the SSH server accepts and manages connections | System administrators     |

This separation allows client and server behavior to be managed independently.

---

## SSH Client Configuration File

The SSH client reads configuration from two possible locations.

### User-Specific Configuration

```text
~/.ssh/config
```

This file affects only the current user.

Each user can maintain their own SSH preferences without affecting other users on the system.

Typical uses include:

* Host aliases
* Default usernames
* Identity files
* Custom ports
* Connection options

#

### System-Wide Client Configuration

```text
/etc/ssh/ssh_config
```

This file applies to all users on the system unless overridden by a user's personal configuration.

System administrators typically use this file to define organization-wide client defaults.

---

## SSH Server Configuration File

The SSH server reads its configuration from:

```text
/etc/ssh/sshd_config
```

This is the primary configuration file for the SSH daemon (`sshd`).

It controls:

* Authentication methods
* Listening ports
* Allowed users
* Root login policy
* Logging
* Port forwarding
* Session behavior
* Security options

Any changes made to this file affect all incoming SSH connections after the configuration is reloaded or the service is restarted.

---

## Configuration File Locations

The following table summarizes the default configuration file locations.

| File                   | Purpose                                |
| ---------------------- | -------------------------------------- |
| `~/.ssh/config`        | User-specific SSH client configuration |
| `/etc/ssh/ssh_config`  | System-wide SSH client configuration   |
| `/etc/ssh/sshd_config` | SSH server configuration               |

Depending on the Linux distribution or OpenSSH version, additional configuration directories may also exist.

---

## Configuration Syntax

OpenSSH configuration files use a simple keyword-value format.

General syntax:

```text
Keyword Value
```

Example:

```text
Port 22
```

Another example:

```text
PasswordAuthentication yes
```

Each configuration directive consists of:

* A keyword
* One or more values

The parser reads the file from top to bottom.

---

## Whitespace

Multiple spaces or tabs between keywords and values are permitted.

Example:

```text
Port 22
```

is equivalent to:

```text
Port        22
```

or

```text
Port    22
```

---

## Comments

Lines beginning with the `#` character are treated as comments.

Example:

```text
# Listen on the default SSH port
Port 22
```

Comments are ignored by OpenSSH.

Comments are useful for:

* Documenting configuration changes
* Temporarily disabling directives
* Explaining configuration choices

Example:

```text
#PasswordAuthentication yes
PasswordAuthentication no
```

---

## Blank Lines

Blank lines have no effect on the configuration.

They are commonly used to improve readability by separating related configuration sections.

Example:

```text
Port 22

PermitRootLogin no

PasswordAuthentication no
```

---

## Case Sensitivity

Configuration keywords are generally **case-insensitive**, but values may be case-sensitive depending on the directive.

**Recommended practice:**

Use the keyword capitalization found in the official OpenSSH documentation.

Example:

```text
PermitRootLogin no
```

---

## Include Directive

Modern versions of OpenSSH support the `Include` directive.

It allows additional configuration files to be loaded.

**Example:**

```text
Include /etc/ssh/sshd_config.d/*.conf
```

or

```text
Include ~/.ssh/config.d/*
```

**Benefits include:**

* Modular configuration
* Easier maintenance
* Separation of custom settings
* Simplified automation

Many Linux distributions use the `sshd_config.d` directory for package-specific or administrator-defined configuration files.

---

## Configuration Processing Order

OpenSSH processes configuration files sequentially.

**For the SSH client:**

1. System-wide client configuration
2. User-specific client configuration

The user's configuration can override system defaults.

**For the SSH server:**

1. `/etc/ssh/sshd_config`
2. Files referenced using the `Include` directive

Understanding the processing order helps predict which settings will take effect.

---

## Testing Configuration

Before applying configuration changes, verify that the configuration syntax is valid.

### Test Server Configuration

```bash
sudo sshd -t
```

If no output is displayed, the configuration is valid.

If errors exist, `sshd` reports the line number and the reason.

**Example:**

```text
Missing argument.
line 47
```

Testing configuration before restarting the service helps prevent accidentally locking yourself out of a remote server.

#

### Display Effective Server Configuration

To display the effective server configuration after all defaults and includes have been processed:

```bash
sudo sshd -T
```

This command is useful for troubleshooting and auditing SSH settings.

---

## Reload Configuration

After modifying the server configuration, apply the changes.

Reload the configuration without stopping the service:

```bash
sudo systemctl reload sshd
```

If reload is not supported or if required by the changes made, restart the service:

```bash
sudo systemctl restart sshd
```

Always verify the service status after reloading or restarting.

```bash
sudo systemctl status sshd
```

---

## File Permissions

Configuration files should be protected against unauthorized modification.

**Typical ownership:**

```text
Owner : root
Group : root
```

**Verify permissions:**

```bash
ls -l /etc/ssh/sshd_config
```

Example:

```text
-rw-r--r--. 1 root root ...
```

Only privileged users should modify the server configuration.

---

## Common Mistakes

### Forgetting to Test Configuration

Always run:

```bash
sudo sshd -t
```

before restarting the SSH service.

#

### Editing the Wrong File

Many administrators mistakenly modify:

```text
/etc/ssh/ssh_config
```

when they intended to change:

```text
/etc/ssh/sshd_config
```

Remember:

* `ssh_config` → Client
* `sshd_config` → Server

#

### Forgetting to Reload the Service

Changes to `sshd_config` do not take effect until the SSH daemon is reloaded or restarted.

---

## Syntax Errors

* Even a small typo can prevent the SSH server from starting.
* Always validate the configuration before applying changes.

---

## Best Practices

* Keep the configuration files well organized.
* Use comments to document important changes.
* Test the configuration before restarting the service.
* Prefer `reload` over `restart` when possible.
* Back up configuration files before making significant changes.
* Use the `Include` directive for modular configurations.
* Limit write access to privileged administrators only.

---

## Summary

OpenSSH relies on separate configuration files for client and server behavior. The client configuration files (`~/.ssh/config` and `/etc/ssh/ssh_config`) define how connections are initiated, while the server configuration file (`/etc/ssh/sshd_config`) controls how the SSH daemon accepts and manages incoming connections.

Understanding where these files are located, how they are structured, and how to safely validate and apply configuration changes is fundamental to effective SSH administration. Individual configuration directives and their practical usage will be explored in dedicated articles later in this roadmap.
