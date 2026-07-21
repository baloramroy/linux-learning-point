## `/var` - Variable Directory

```
/var/
├── account/                     # Process accounting logs
├── cache/                       # Application cache data (re-creatable)
│   ├── man/                     # Cached man page indexes
│   ├── dnf/                     # DNF package manager cache
│   ├── yum/                     # YUM cache (legacy)
│   └── ldconfig/                # Shared library cache
├── crash/                       # Kernel & application crash dumps
├── db/                          # Small local databases (rare today)
├── empty/                       # Empty dir for privilege separation (sshd)
├── games/                       # Variable game data (scores, saves)
├── lib/                         # Persistent application state data
│   ├── docker/                  # Docker runtime data
│   │   ├── containers/          # Container metadata
│   │   ├── image/               # Docker images
│   │   ├── overlay2/            # Container filesystem layers
│   │   └── volumes/             # Docker volumes
│   ├── mysql/                   # MySQL/MariaDB databases
│   ├── pgsql/                   # PostgreSQL databases
│   ├── rpm/                     # RPM package database
│   ├── systemd/                 # systemd state data
│   ├── selinux/                 # SELinux runtime data
│   └── yum/                     # YUM history and state
├── local/                       # Variable data for /usr/local
├── lock/                        # Lock files (symlink to /run/lock)
├── log/                         # System and application logs
│   ├── audit/                   # Audit subsystem logs
│   │   └── audit.log            # SELinux & security audit log
│   ├── chrony/                  # NTP logs
│   ├── cups/                    # Printing logs
│   ├── httpd/                   # Apache logs
│   ├── nginx/                   # NGINX logs
│   ├── journal/                 # systemd journal logs
│   ├── messages                 # General system messages
│   ├── secure                   # Authentication & security logs
│   └── wtmp                     # Login/logout history
├── mail/                        # User mailboxes
├── opt/                         # Variable data for /opt software
├── preserve/                    # Files preserved during upgrades
├── run/                         # Runtime data since boot (symlink to /run)
│   ├── systemd/                 # systemd runtime state
│   └── user/                    # Per-user runtime data
├── spool/                       # Queued tasks waiting for processing
│   ├── cron/                    # Cron job queues
│   ├── at/                      # at job queues
│   ├── mail/                    # Mail queue
│   ├── postfix/                 # Postfix mail queue
│   └── cups/                    # Print jobs
├── tmp/                         # Temporary files (persist after reboot)
└── www/                         # Web server document root (legacy)
```

---

### One-line exam memory hook

> **`/var` = everything that grows, changes, or gets written while the system runs**

---
