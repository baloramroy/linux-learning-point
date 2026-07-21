## `/etc/` – Configuration Files Structure


```
/etc/
├── passwd                          # User account database
├── group                           # Group definitions
├── shadow                          # Secure user password hashes (root only)
├── hosts                           # Static hostname-to-IP mappings
├── hostname                        # System hostname
├── fstab                           # Filesystem mount table
├── sudoers                         # Sudo privileges configuration
├── crontab                         # System-wide cron jobs
├── shell                           # List of valid login shells
├── profile                         # System-wide environment/profile settings
├── nsswitch.conf                   # Name Service Switch configuration
├── resolv.conf                     # DNS resolver configuration
├── locale.conf                     # System locale settings
├── timezone                        # System timezone (symbolic link)
│
├── ssh/                            # SSH configuration
│   ├── sshd_config                 # SSH server configuration
│   ├── ssh_config                  # SSH client configuration
│   └── ssh_host_*_key              # SSH host keys
│
├── systemd/                        # Systemd init system
│   ├── system.conf                 # Systemd manager configuration
│   ├── user.conf                   # Per-user systemd configuration
│   ├── system/                     # System service units
│   │   ├── sshd.service            # SSH service unit
│   │   ├── nginx.service           # Web server service unit
│   │   └── *.service.d/            # Service drop-in directories
│   └── network/                    # Network configuration
│
├── yum.repos.d/                    # YUM/DNF repositories (RHEL/Fedora)
│   └── *.repo                      # Individual repository files
│
├── nginx/                          # Nginx web server
│   ├── nginx.conf                  # Main configuration
│   ├── sites-available/            # Available website configurations
│   ├── sites-enabled/              # Enabled websites (symlinks)
│   └── conf.d/                     # Additional configuration snippets
│
├── security/                       # Security settings
│   ├── limits.conf                 # User resource limits
│   ├── pam.conf                    # Pluggable Authentication Modules
│   └── access.conf                 # Login access control
│
├── cron.d/                         # System cron jobs
│   ├── hourly/                     # Hourly cron scripts
│   ├── daily/                      # Daily cron scripts
│   ├── weekly/                     # Weekly cron scripts
│   └── monthly/                    # Monthly cron scripts
│
├── logrotate.d/                    # Log rotation configuration
│   └── *.conf                      # Application-specific logrotate configs
│
├── network/                        # Network configuration (traditional)
│   ├── interfaces                  # Network interface configuration
│   └── if-up.d/, if-down.d/        # Interface up/down scripts
│
├── NetworkManager/                 # NetworkManager daemon
│   ├── NetworkManager.conf         # Main configuration
│   └── system-connections/         # Stored network connection profiles
│
├── fonts/                          # Font configuration
│   ├── fonts.conf                  # Font configuration
│   └── conf.d/                     # Additional font configurations
|
├── docker/                         # Docker container engine
│   └── daemon.json                 # Docker daemon configuration
│
├── selinux/                        # SELinux security framework
│   ├── config                      # SELinux mode (enforcing/permissive/disabled)
│   └── contexts/                   # Security contexts
│
├── pam.d/                          # PAM service configurations
│   ├── login                       # Login authentication
│   ├── sshd                        # SSH authentication
│   └── sudo                        # Sudo authentication
│
└── ssl/                            # SSL certificates
    ├── certs/                      # Certificate files
    │   └── ca-certificates.crt     # CA certificate bundle
    └── private/                    # Private keys (restricted permissions)

```
