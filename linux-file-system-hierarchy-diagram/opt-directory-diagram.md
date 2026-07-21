## **/opt** – Optional software packages

```
/opt/
├── google/
│   ├── chrome/
│   │   ├── chrome                     # Main executable
│   │   ├── chrome_crashpad_handler    # Crash handler
│   │   ├── lib/                       # Shared libraries
│   │   │   ├── libchrome.so
│   │   │   └── libv8.so
│   │   ├── resources/                 # Application resources
│   │   │   ├── locales/               # Language packs
│   │   │   ├── 100_percent.pak        # UI resources
│   │   │   └── chrome_100_percent.pak
│   │   └── WIDEVINE.CDM               # DRM component
│   └── cloud-sdk/
│       ├── bin/                       # Google Cloud CLI tools
│       │   ├── gcloud
│       │   ├── gsutil
│       │   └── bq
│       ├── lib/                       # SDK libraries
│       └── install.log
├── microsoft/
│   ├── teams/
│   │   ├── teams                     # Main executable
│   │   ├── resources/                # App resources
│   │   ├── chrome_100_percent.pak
│   │   └── chrome_200_percent.pak
│   └── vscode/
│       ├── bin/code                  # Visual Studio Code launcher
│       ├── resources/app/            # VS Code core
│       └── resources/app.asar
├── oracle/
│   ├── java/
│   │   ├── jdk-17/                   # JDK installation
│   │   │   ├── bin/java
│   │   │   ├── lib/rt.jar
│   │   │   └── conf/                 # Java configuration
│   │   └── jre-8/                    # JRE installation
│   └── virtualbox/
│       ├── VBoxManage                # CLI utility
│       ├── VirtualBox                # GUI executable
│       ├── ExtensionPacks/           # VirtualBox extensions
│       └── drivers/                  # Hardware drivers
├── jetbrains/
│   ├── idea-IC/                      # IntelliJ IDEA Community
│   │   ├── bin/idea.sh               # Launcher script
│   │   ├── lib/                      # IntelliJ libraries
│   │   └── plugins/                  # IDE plugins
│   └── toolbox/                      # JetBrains Toolbox App
├── nvidia/
│   ├── cuda/                         # CUDA Toolkit
│   │   ├── bin/nvcc                  # CUDA compiler
│   │   ├── lib64/libcudart.so        # CUDA runtime
│   │   └── samples/                  # CUDA samples
│   └── nvidia_driver/                # Proprietary driver utils
├── vmware/
│   ├── vmware-workstation/
│   │   ├── bin/vmware                # Main executable
│   │   └── lib/vmware/               # VM libraries
│   └── vmware-player/
├── adobe/
│   ├── acrobat/
│   └── reader/
├── matlab/
│   ├── R2023a/                       # MATLAB version
│   │   ├── bin/matlab                # MATLAB launcher
│   │   ├── toolbox/                  # MATLAB toolboxes
│   │   └── sys/os/glnxa64/           # OS-specific binaries
│   └── installer/                    # MATLAB installer cache
├── slack/
│   ├── slack                         # Executable
│   └── resources/app.asar.unpacked/
├── sublime_text/
│   ├── sublime_text                  # Editor executable
│   ├── Packages/                     # Installed packages
│   └── libpython3.3.so.1.0
├── zoom/
│   ├── zoom                          # Client executable
│   ├── zopen                         # Opening utility
│   └── QtWebEngine/                  # Embedded browser engine
└── README                            # Optional: directory info
```

## **Related Directories** (FHS Compliance)

```
/var/opt/                             # Variable data for /opt packages
├── google/
│   ├── chrome/                       # Chrome user data, cache
│   └── cloud-sdk/                    # Cloud SDK config, logs
├── microsoft/
│   ├── teams/logs/                   # Teams application logs
│   └── vscode/logs/                  # VS Code logs
├── oracle/
│   ├── java/logs/                    # Java usage logs
│   └── virtualbox/                   # VM configurations, logs
└── nvidia/cuda/logs/                 # CUDA compilation logs

/etc/opt/                             # Configuration for /opt packages
├── google/
│   └── chrome/                       # System-wide Chrome policies
├── microsoft/
│   └── teams/policies.json           # Teams admin policies
├── oracle/java/jdk-17.conf           # Java system configuration
└── nvidia/cuda/cuda.conf             # CUDA system settings
```

