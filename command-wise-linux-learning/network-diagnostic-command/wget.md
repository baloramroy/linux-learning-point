
# `wget` - Non-interactive downloading of files

The **wget** command is used for non-interactive downloading of files from HTTP, HTTPS, and FTP servers.

---

### Basic wget Commands

- Download a file using its original name

  ```bash
  wget https://example.com/file.txt
  ```
  
  **Output:**
  Creates `file.txt` in the current directory.

- Download a file and save it with a custom filename

  ```bash
  wget -O newfile.txt https://example.com/file.txt
  ```
  
  **Output:**
  Creates a file named `newfile.txt`.

- Download multiple files from a list
  
  ```bash
  wget -i filelist.txt
  ```
  
  **Output:**
  Downloads all URLs written in `filelist.txt`.

---

### Advance Download Control Options

- Resume an interrupted download
  
  ```bash
  wget -c https://example.com/largefile.iso
  ```
  
  **Output:**
  Continues downloading where it left off.
  
- Limit download speed
  
  ```bash
  wget --limit-rate=200k https://example.com/file.iso
  ```
  
  **Output:**
  Download proceeds at maximum **200 KB/s**.
  
- Retry download automatically
  
  ```bash
  wget --tries=10 https://example.com/file.zip
  ```
  
  **Output:**
  `wget` retries **10 times** before giving up.
  
- Hide all output except errors (silent mode)
  
  ```bash
  wget -q https://example.com/file.zip
  ```
  
  **Output:**
  No progress or logs; only errors appear.
  
- Show download progress bar in dot format
  
  ```bash
  wget --progress=dot https://example.com/file.zip
  ```
  
  **Output:**
  Shows download progress as moving dots.

---

### SSL/TLS Related

- Ignore invalid SSL certificates

  ```bash
  wget --no-check-certificate https://example.com
  ```
  
  **Output:**
  Site content loads even if SSL certificate is invalid.

---

### Website Download Commands

- Download an entire website (mirror)

  ```bash
  wget --mirror https://example.com
  ```
  
  **Output:**
  Creates a full offline clone of the site.

- Download website recursively, keeping folder structure

  ```bash
  wget -r https://example.com
  ```
  
  **Output:**
  Downloads all linked pages and directories.

- Download a website for offline browsing (with assets)
  
  ```bash
  wget -r -k -p https://example.com
  ```
  
  **Output:**
  A complete offline-browsable website with images, CSS, JS.

---

### Proxy Related Commands

- Use a proxy server for downloading
  
  ```bash
  wget -e use_proxy=yes -e http_proxy=http://proxy:8080 https://example.com/file.txt
  ```
  
  **Output:**
  File downloaded through proxy.

---

### Timeout & Retry Handling

- Set download timeout
  
  ```bash
  wget --timeout=10 https://example.com/file.zip
  ```
  
  **Output:**
  Fails if no response within **10 seconds**.
  
- Retry download on network failures
  
  ```bash
  wget --retry-connrefused https://example.com/file.txt
  ```
  
  **Output:**
  Retries if the server refuses connection.

---

### Network & Troubleshooting

- Check if a URL is reachable (no download)

  ```bash
  wget --spider https://example.com
  ```
  
  **Output:**
  Reports “200 OK” or errors.
  **Purpose:**
  Troubleshoot connectivity, verify URL works.

---

### FTP Download Commands

- Download file from an FTP server

  ```bash
  wget ftp://example.com/file.zip
  ```
  
  **Output:**
  Downloads file via FTP.

---

