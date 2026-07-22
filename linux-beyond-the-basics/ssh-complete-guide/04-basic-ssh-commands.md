# Basic SSH Commands

## Introduction

The OpenSSH client provides a collection of commands for securely connecting to remote systems, executing commands, transferring files, and managing SSH sessions.

Among these, the `ssh` command is the primary tool used for establishing encrypted remote connections. By combining various command-line options, users can customize how connections are established and how remote tasks are performed.

This article introduces the most commonly used SSH commands and options. Advanced topics such as SSH configuration files, key-based authentication, port forwarding, tunneling, and SSH agents will be covered in later articles.

---

## SSH Command Syntax

The basic syntax of the SSH command is:

```bash
ssh [OPTIONS] [USER@]HOST [COMMAND]
```

Where:

| Component | Description                                 |
| --------- | ------------------------------------------- |
| `ssh`     | OpenSSH client command                      |
| `OPTIONS` | Command-line options                        |
| `USER`    | Username on the remote system               |
| `HOST`    | Hostname or IP address of the remote system |
| `COMMAND` | Optional command to execute remotely        |

---

## Connect to a Remote Server

The simplest SSH command connects to a remote server.

```bash
ssh user@server
```

Example:

```bash
ssh admin@192.168.1.10
```

or

```bash
ssh admin@example.com
```

If authentication succeeds, an interactive shell session is opened on the remote machine.

---

## Connect Using the Current Username

If the local username matches the remote username, the username can be omitted.

```bash
ssh server
```

Example:

```bash
ssh server01
```

SSH automatically attempts to log in using the current local username.

---

## Connect Using an IP Address

Instead of a hostname, you can specify an IPv4 or IPv6 address.

```bash
ssh user@192.168.1.100
```

Example:

```bash
ssh root@10.10.10.25
```

---

## Connect Using a Different Port

By default, SSH listens on **TCP port 22**.

If the server uses a different port, specify it using the `-p` option.

```bash
ssh -p PORT user@server
```

Example:

```bash
ssh -p 2222 admin@192.168.1.10
```

---

## Execute a Remote Command

SSH can execute a single command without opening an interactive shell.

```bash
ssh user@server "command"
```

Example:

```bash
ssh admin@server01 "hostname"
```

Output:

```text
server01
```

Another example:

```bash
ssh admin@server01 "uptime"
```

Once the command finishes, the SSH session closes automatically.

---

## Execute Multiple Commands

Multiple commands can be executed in a single SSH session.

```bash
ssh user@server "command1; command2; command3"
```

Example:

```bash
ssh admin@server01 "hostname; uptime; whoami"
```

---

## Login with a Specific Identity File

Specify a private key manually.

```bash
ssh -i private_key user@server
```

Example:

```bash
ssh -i ~/.ssh/id_ed25519 admin@server01
```

Key-based authentication will be discussed in detail in a later article.

---

## Enable Verbose Output

Verbose mode helps troubleshoot SSH connection problems.

### Level 1

```bash
ssh -v user@server
```

Displays basic connection information.

#

### Level 2

```bash
ssh -vv user@server
```

Provides more detailed debugging information.

#

### Level 3

```bash
ssh -vvv user@server
```

Displays maximum debugging output.

This is commonly used when troubleshooting authentication failures.

---

## Display SSH Client Version

Display the installed OpenSSH client version.

```bash
ssh -V
```

Example:

```text
OpenSSH_9.7p1
```

---

## Disable Pseudo-Terminal Allocation

Some automation tasks do not require an interactive terminal.

```bash
ssh -T user@server
```

Example:

```bash
ssh -T git@github.com
```

---

## Force Terminal Allocation

Some commands require an interactive terminal.

Use:

```bash
ssh -t user@server
```

Example:

```bash
ssh -t admin@server01 "top"
```

---

## Run Commands as Another User

Example:

```bash
ssh admin@server01 "sudo systemctl status nginx"
```

If passwordless sudo is not configured, the remote system prompts for the sudo password.

---

## Compress Network Traffic

Enable SSH compression.

```bash
ssh -C user@server
```

Compression can improve performance on slow network connections.

---

## Specify Connection Timeout

Set a timeout for establishing the connection.

```bash
ssh -o ConnectTimeout=10 user@server
```

If the connection is not established within ten seconds, SSH exits.

---

## Ignore Host Key Checking (Temporary)

```bash
ssh -o StrictHostKeyChecking=no user@server
```

This option automatically accepts unknown host keys.

> **Warning:** Disabling host key verification reduces security and should only be used in controlled environments such as testing or automation where appropriate safeguards are in place.

---

## Connect Quietly

Suppress most warning messages.

```bash
ssh -q user@server
```

Useful for scripts.

---

## Exit an SSH Session

To leave an interactive SSH session:

```bash
exit
```

or

```bash
logout
```

Keyboard shortcut:

```text
Ctrl + D
```

---

## Common SSH Command Options

| Option | Description                        |
| ------ | ---------------------------------- |
| `-p`   | Specify SSH port                   |
| `-i`   | Specify identity file              |
| `-v`   | Verbose output                     |
| `-vv`  | More verbose output                |
| `-vvv` | Maximum debugging output           |
| `-C`   | Enable compression                 |
| `-t`   | Force pseudo-terminal allocation   |
| `-T`   | Disable pseudo-terminal allocation |
| `-q`   | Quiet mode                         |
| `-o`   | Specify additional SSH options     |
| `-V`   | Display SSH version                |

---

## Practical Examples

### Connect to a server

```bash
ssh admin@192.168.10.15
```

#

### Connect using port 2222

```bash
ssh -p 2222 admin@192.168.10.15
```

#

### Execute a command remotely

```bash
ssh admin@server01 "df -h"
```

#

### Restart a service remotely

```bash
ssh admin@server01 "sudo systemctl restart httpd"
```

#

### View remote log entries

```bash
ssh admin@server01 "tail -20 /var/log/messages"
```

#

### Check system uptime

```bash
ssh admin@server01 "uptime"
```

#

### Determine the current user

```bash
ssh admin@server01 "whoami"
```

---

## Common Mistakes

### Using the Wrong Port

If the server listens on a custom port, specify it with the `-p` option.

#

### Forgetting the Username

Different servers may require different usernames such as:

* root
* admin
* ec2-user
* ubuntu
* centos

#

### Ignoring Verbose Output

When troubleshooting connection issues, use:

```bash
ssh -vvv
```

It often provides enough information to identify the problem.

#

### Executing Interactive Programs Without a Terminal

Programs such as `top`, `nano`, or `vi` require a pseudo-terminal.

Use:

```bash
ssh -t
```

---

## Best Practices

* Use hostnames instead of IP addresses whenever possible.
* Prefer key-based authentication over passwords.
* Use verbose mode when troubleshooting.
* Verify the remote host before accepting its host key.
* Avoid disabling host key verification unless absolutely necessary.
* Use connection timeouts in automation scripts.
* Keep SSH client software updated.

---

## Summary

The `ssh` command is the primary interface for securely accessing remote Linux systems. By understanding its basic syntax and commonly used options, administrators can connect to remote hosts, execute commands, troubleshoot connectivity issues, and automate routine administrative tasks.

As you progress through the SSH roadmap, these basic commands will serve as the foundation for more advanced topics such as key management, SSH configuration, authentication, port forwarding, tunneling, and automation.
