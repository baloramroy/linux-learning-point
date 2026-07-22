# Installing OpenSSH

## Introduction

OpenSSH (Open Secure Shell) is the most widely used implementation of the SSH protocol. It provides secure remote login, encrypted file transfer, remote command execution, and secure tunneling over unsecured networks.

OpenSSH consists of two main components:

* **OpenSSH Client** – Used to initiate SSH connections to remote systems.
* **OpenSSH Server** – Accepts incoming SSH connections and allows remote access to the system.

Most Linux distributions include the OpenSSH client by default, while the OpenSSH server package may need to be installed separately.

#

# Installing OpenSSH Server

The OpenSSH server package provides the `sshd` (SSH Daemon) service, which listens for incoming SSH connections.

## RHEL, CentOS, Rocky Linux, AlmaLinux

Install the server package using `dnf`:

```bash
sudo dnf install openssh-server
```

For older versions:

```bash
sudo yum install openssh-server
```

#

## Ubuntu and Debian

```bash
sudo apt update
sudo apt install openssh-server
```

#

## SUSE Linux

```bash
sudo zypper install openssh
```

#

## Verify Installation

After installation, verify that the package is installed.

### RHEL-based Systems

```bash
rpm -q openssh-server
```

Example:

```text
openssh-server-9.x.x
```

### Debian-based Systems

```bash
dpkg -l | grep openssh-server
```

#

# Installing OpenSSH Client

The client package allows a system to connect to remote SSH servers.

In many Linux distributions, it is installed by default. If not, install it using the appropriate package manager.

## RHEL, CentOS, Rocky Linux, AlmaLinux

```bash
sudo dnf install openssh-clients
```

Older systems:

```bash
sudo yum install openssh-clients
```

#

## Ubuntu and Debian

```bash
sudo apt update
sudo apt install openssh-client
```

#

## SUSE Linux

```bash
sudo zypper install openssh
```

#

# Verify Client Installation

Check whether the SSH client is available.

```bash
ssh
```

or

```bash
which ssh
```

Example output:

```text
/usr/bin/ssh
```

#

# Check SSH Version

To display the installed OpenSSH client version:

```bash
ssh -V
```

Example:

```text
OpenSSH_9.7p1, OpenSSL 3.2.2
```

> **Note:** The version information is written to **stderr**, so this command may behave differently in scripts.

To verify the server version:

```bash
sshd -V
```

Depending on the distribution, this may also print to **stderr**.

#

# Enable SSH Service

After installing the server package, enable the SSH service so it starts automatically during system boot.

```bash
sudo systemctl enable sshd
```

Example output:

```text
Created symlink /etc/systemd/system/multi-user.target.wants/sshd.service → /usr/lib/systemd/system/sshd.service
```

#

# Start SSH Service

Start the SSH server immediately without rebooting.

```bash
sudo systemctl start sshd
```

#

# Stop SSH Service

To stop the SSH service:

```bash
sudo systemctl stop sshd
```

Stopping the SSH service disconnects new incoming SSH connections. Existing sessions may also terminate depending on the system configuration.

#

# Restart SSH Service

Restart the service after making configuration changes.

```bash
sudo systemctl restart sshd
```

This stops and starts the service again.

#

# Reload SSH Configuration

If only the configuration file has changed, reload the service instead of restarting it.

```bash
sudo systemctl reload sshd
```

Reloading applies configuration changes without completely restarting the daemon, when supported.

#

# Check SSH Service Status

Display the current service status.

```bash
sudo systemctl status sshd
```

Example:

```text
● sshd.service - OpenSSH server daemon
     Loaded: loaded
     Active: active (running)
```

The status output provides information such as:

* Service state
* Main process ID (PID)
* Startup time
* Recent log messages

#

# Check Whether SSH Is Listening

Verify that the SSH server is listening for incoming connections.

Using `ss`:

```bash
sudo ss -tlnp | grep sshd
```

Example:

```text
LISTEN 0 128 0.0.0.0:22
```

Alternatively:

```bash
sudo ss -tlnp | grep :22
```

#

# Verify Firewall Access

If a firewall is enabled, ensure SSH traffic is allowed.

Example using `firewalld`:

```bash
sudo firewall-cmd --list-services
```

Expected output:

```text
cockpit dhcpv6-client ssh
```

If SSH is not allowed:

```bash
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```

#

# Verify SELinux (RHEL-based Systems)

If SELinux is enabled and SSH is configured to use a non-default port, verify that SELinux permits the port.

Check the current SSH port:

```bash
sudo semanage port -l | grep ssh
```

> This topic will be covered in more detail in the SSH Server Configuration article.

#

# Test the SSH Server

If testing locally:

```bash
ssh localhost
```

or

```bash
ssh 127.0.0.1
```

If testing from another machine:

```bash
ssh username@server-ip
```

Example:

```bash
ssh admin@192.168.1.10
```

If the connection succeeds, the server is installed and functioning correctly.

#

# Common Installation Issues

## SSH service is not running

Symptoms:

```text
Connection refused
```

Possible solution:

```bash
sudo systemctl start sshd
```

#

## OpenSSH server package is not installed

Symptoms:

```text
Unit sshd.service could not be found
```

Possible solution:

Install the OpenSSH server package using the appropriate package manager.

#

## Firewall blocks SSH

Symptoms:

```text
Connection timed out
```

Possible solution:

Allow the SSH service through the firewall.

#

## Incorrect SSH Port

If the server has been configured to use a different port, specify it when connecting.

Example:

```bash
ssh -p 2222 username@server-ip
```

#

# Best Practices

* Keep OpenSSH updated with security patches.
* Enable the SSH service only when remote access is required.
* Verify the service status after installation.
* Test connectivity immediately after installation.
* Use `systemctl reload sshd` after configuration changes when appropriate.
* Ensure firewall rules permit SSH traffic.
* Verify SELinux settings when using custom SSH ports.
* Avoid modifying the default configuration until the installation has been verified.

#

# Summary

Installing OpenSSH involves installing the appropriate client and server packages, verifying the installation, enabling and starting the `sshd` service, confirming that the service is listening for connections, and testing remote access. Once the installation has been verified, the system is ready for further configuration, including authentication methods, configuration files, and security hardening, which are covered in subsequent articles.
