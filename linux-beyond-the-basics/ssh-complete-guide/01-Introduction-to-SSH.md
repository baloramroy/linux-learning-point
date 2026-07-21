# Introduction to SSH

## Introduction

Secure Shell (SSH) is a cryptographic network protocol used to securely access and manage remote systems over an unsecured network. It provides encrypted communication between a client and a server, ensuring that sensitive information such as usernames, passwords, commands, and transferred data cannot be easily intercepted or modified by unauthorized parties.

SSH has become the de facto standard for remote system administration on Linux and UNIX-like operating systems. It is widely used by system administrators, DevOps engineers, cloud engineers, network administrators, and developers for securely managing servers, automating tasks, transferring files, and creating encrypted network tunnels.

The protocol was designed to replace insecure remote access protocols such as Telnet, rlogin, and rsh, which transmitted data in plain text and exposed users to credential theft and other security risks.

---

## What is SSH?

**SSH (Secure Shell)** is a secure network protocol that enables encrypted communication between two computers over a network.

It follows a **client-server architecture**, where:

* An SSH client initiates a connection.
* An SSH server accepts and manages incoming SSH connections.

Once the connection is established, the client can securely:

* Log in to a remote system
* Execute commands remotely
* Transfer files
* Forward network ports
* Tunnel network traffic
* Automate administrative tasks

SSH primarily operates over **TCP port 22**, although administrators can configure it to use a different port.

---

## Why SSH is Used

SSH is used because it provides a secure method for remote communication.

Without SSH, administrative tasks performed across a network could expose sensitive information to attackers.

Common reasons for using SSH include:

* Secure remote server administration
* Secure command execution
* Secure file transfer
* Remote application management
* Infrastructure automation
* Git repository access
* Cloud server management
* Database administration
* Network device management
* Secure tunneling of network services

SSH protects communication by encrypting all transmitted data.

---

## SSH vs Telnet

Before SSH became the industry standard, Telnet was commonly used for remote administration.

The biggest difference between them is **security**.

| Feature               | SSH       | Telnet      |
| --------------------- | --------- | ----------- |
| Encryption            | Yes       | No          |
| Authentication        | Secure    | Plain text  |
| Data Protection       | Encrypted | Unencrypted |
| Default Port          | 22        | 23          |
| Suitable for Internet | Yes       | No          |
| Integrity Checking    | Yes       | No          |
| Confidentiality       | Yes       | No          |

#

### Telnet

Telnet sends everything in plain text.

This includes:

* Username
* Password
* Commands
* Output

Anyone capturing network traffic can read the transmitted information.

#

### SSH

- SSH encrypts the entire communication channel before any sensitive information is exchanged.

- Even if network traffic is captured, the transmitted data appears as unreadable encrypted data.

- Because of this, SSH has almost completely replaced Telnet in modern environments.

---

## SSH Architecture

SSH follows a **client-server architecture**.

```text
+----------------+                     +----------------+
|                |                     |                |
|   SSH Client   | <---- Encrypted --->|   SSH Server   |
|                |                     |                |
+----------------+                     +----------------+
```

The communication process consists of three logical layers.

1. Transport Layer
2. User Authentication Layer
3. Connection Layer

### Transport Layer

The Transport Layer is responsible for:

* Establishing a secure connection
* Negotiating encryption algorithms
* Performing key exchange
* Encrypting communication
* Protecting data integrity

### User Authentication Layer

This layer verifies the identity of the user attempting to connect.

Authentication methods include:

* Password authentication
* Public key authentication
* Keyboard-interactive authentication
* Host-based authentication
* Certificate authentication

### Connection Layer

Once authentication succeeds, the Connection Layer manages:

* Interactive shell sessions
* Remote command execution
* Port forwarding
* File transfer sessions
* Multiple logical channels over a single SSH connection

---

## SSH Components

SSH consists of two primary components.

### SSH Client

The SSH client is the software used to initiate a secure connection to a remote system.

Examples include:

* OpenSSH Client
* PuTTY
* MobaXterm
* Windows OpenSSH Client

Responsibilities of the SSH client include:

* Initiating the connection
* Negotiating encryption
* Authenticating the user
* Sending commands
* Receiving responses

Example:

```bash
ssh user@192.168.1.100
```

#

### SSH Server

The SSH server listens for incoming SSH connections and provides secure remote access.

On Linux, the server software is typically **OpenSSH Server**, whose daemon is called:

```text
sshd
```

The SSH server is responsible for:

* Accepting client connections
* Authenticating users
* Encrypting communication
* Authorizing access
* Executing commands
* Managing SSH sessions

---

## SSH Workflow

The following sequence illustrates how a typical SSH connection is established.

```text
Client                         Server
  |                               |
  |------ TCP Connection --------->|
  |                               |
  |<----- SSH Version ------------ |
  |                               |
  |--- Algorithm Negotiation ----->|
  |                               |
  |<------ Key Exchange ---------->|
  |                               |
  |<---- Host Verification ------->|
  |                               |
  |------ User Authentication ---->|
  |                               |
  |<---- Authentication Success ---|
  |                               |
  |====== Encrypted Session ======>|
```

The workflow can be summarized as follows:

1. The client establishes a TCP connection.
2. The client and server exchange SSH protocol versions.
3. Both systems negotiate supported encryption algorithms.
4. A secure key exchange occurs.
5. The client verifies the server's identity.
6. The user is authenticated.
7. An encrypted session is established.
8. Commands and data are securely exchanged.

---

## SSH Encryption Basics

SSH uses multiple cryptographic techniques rather than relying on a single encryption method.

### Symmetric Encryption

Symmetric encryption uses the **same secret key** for both encryption and decryption.

After the secure session has been established, symmetric encryption is used because it is fast and efficient.

Common algorithms include:

* AES
* ChaCha20

#

### Asymmetric Encryption

Asymmetric encryption uses a **public key** and a **private key**.

It is primarily used for:

* Identity verification
* Secure key exchange
* Public key authentication

The private key remains secret, while the public key can be safely shared.

Common algorithms include:

* RSA
* ECDSA
* Ed25519

#

### Hashing

Hash functions generate a fixed-length output from data.

SSH uses hashing to verify that transmitted data has not been modified.

Common algorithms include:

* SHA-2 family

#

### Message Authentication Code (MAC)

A Message Authentication Code (MAC) ensures:

* Data integrity
* Message authenticity

It allows the receiving system to detect whether transmitted data has been altered during transmission.

---

## SSH Authentication Methods

SSH supports several authentication mechanisms.

### Password Authentication

The user enters a username and password.

The server verifies the credentials before granting access.

Advantages:

* Simple
* Easy to configure

Disadvantages:

* Vulnerable to brute-force attacks if not properly protected.

#

### Public Key Authentication

Public key authentication uses a cryptographic key pair.

* Public key → Stored on the server.
* Private key → Stored securely by the client.

This method is significantly more secure than password authentication and is widely used in production environments.

#

### Keyboard-Interactive Authentication

The server interacts with the user by presenting one or more authentication prompts.

This method is commonly integrated with systems such as:

* PAM (Pluggable Authentication Modules)
* Multi-Factor Authentication (MFA)

#

### Host-Based Authentication

Host-based authentication allows one trusted host to authenticate on behalf of its users.

It is mainly used in controlled enterprise environments.

#

### Certificate Authentication

Instead of trusting individual public keys, SSH can authenticate users using digital certificates issued by a trusted Certificate Authority (CA).

This approach simplifies key management in large environments.

---

## SSH Versions

Two major versions of SSH have existed.

### SSH-1

SSH-1 was the original implementation.

Although it introduced encrypted remote communication, it contains several known security weaknesses.

SSH-1 is now considered obsolete and should not be used.


### SSH-2

SSH-2 is the modern standard.

It provides:

* Stronger encryption
* Improved integrity protection
* Better authentication mechanisms
* Enhanced security
* Improved protocol design
* Better extensibility

Almost all modern Linux distributions support SSH-2.

---

## SSH-1 vs SSH-2

| Feature              | SSH-1   | SSH-2             |
| -------------------- | ------- | ----------------- |
| Release              | Older   | Current Standard  |
| Security             | Weak    | Strong            |
| Encryption           | Limited | Modern Algorithms |
| Authentication       | Basic   | Multiple Methods  |
| Integrity Protection | Limited | Improved          |
| Recommended          | No      | Yes               |

SSH-2 should always be used for new deployments.

---

# Summary

SSH is the industry-standard protocol for secure remote communication. It replaces insecure protocols such as Telnet by encrypting all communication between a client and a server.

Understanding the fundamental concepts of SSH—including its architecture, workflow, encryption mechanisms, authentication methods, and protocol versions—provides the foundation for more advanced topics such as OpenSSH installation, SSH configuration, key management, port forwarding, tunneling, and server hardening.
