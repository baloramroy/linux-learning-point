## **Typical Structure Inside a User's Home:**

```
/home/username/
├── Desktop/                    # Desktop files (GUI environments)
├── Documents/                  # Personal documents
├── Downloads/                  # Downloaded files
├── Music/, Pictures/, Videos/  # Media files
├── Public/                     # Files shared with other users
├── Templates/                  # Document templates
│
├── .bashrc                     # Bash shell configuration
├── .profile                    # Login shell profile
├── .bash_history               # Command history
│
├── .ssh/                       # SSH keys and config (permissions: 700)
│   ├── id_rsa                  # Private key (600)
│   ├── id_rsa.pub              # Public key (644)
│   └── known_hosts             # Known SSH hosts
│
├── .config/                    # Application configurations (XDG standard)
│   ├── code/                   # VS Code settings
│   ├── chromium/               # Browser settings
│   └── user-dirs.dirs          # Localized directory names
│
├── .cache/                     # Temporary cache files (can be deleted)
├── .local/share/               # Application data (XDG data home)
├── .mozilla/                   # Firefox profile (older convention)
│
└── .gnupg/                     # GnuPG encryption keys
```
