# `curl` Command

The purpose of the **curl** command is to transfer data to or from a server using various **network protocols**.
It is a command-line tool that allows users to **interact** with **web servers** and **APIs**, **download** and **upload** files, and automate internet data transfer.

---

### Basic `curl` Commands

- Fetch and display a webpage or API response directly in the terminal
  
  ```bash
  curl https://example.com
  ```
  
  **Output:**
  HTML or JSON printed on terminal.
  
- Download a remote file and save it using the original filename
  
  ```bash
  curl -O https://example.com/file.txt
  ```
  
  **Output:**
  A file named `file.txt` appears in the current directory.
  
- Download a file and save it using a custom filename
  
  ```bash
  curl -o output.txt https://example.com/file.txt
  ```
  
  **Output:**
  A file named `output.txt` is created.

---

### Silent, Fail, Redirect Options of curl Command

- Fetches the content quietly without showing progress bar or status messages
  
  ```bash
  curl -s https://example.com
  ```
  
  **Output:**
  Only the response body is shown.
  
- Run curl silently but still display any error messages
  
  ```bash
  curl -sS https://example.com
  ```
  
  **Output:**
  Quiet output, but shows errors like 404/500.
  
- Stop and return an error when the server responds with an HTTP error code
  
  ```bash
  curl -f https://example.com
  ```
  
  **Output:**
  No output if server returns error; curl exits with non-zero code.
  
  **Purpose:**
  Prevents accidentally saving error pages.
  
- Automatically follow URL redirects until the final destination is reached
  
  ```bash
  curl -L https://short.url
  ```
  
  **Output:**
  Content from the final redirected URL.
  
  **Purpose:**
  Required for shortened links, moved pages, or dynamic redirects.

---

### Authentication

- Send a username and password for websites or APIs that require basic authentication

  ```bash
  curl -u user:password https://example.com
  ```
  
  **Output:**
  Server response after successful authentication.

---

### SSL/TLS Related Commands

- Connect to an HTTPS site while ignoring certificate validation errors

  ```bash
  curl -k https://example.com
  ```
  
  **Output:**
  Content is shown even if SSL certificate is invalid or expired.

- Display detailed SSL handshake and HTTP response header information

  ```bash
  curl -vI https://example.com
  ```
  
  **Output:**
  SSL details + HTTP headers.
  
  **Purpose:**
  Troubleshooting SSL/TLS problems and verifying certificate details.

---

### Debug / Troubleshooting Options

- Show detailed request and response including headers and connection information
  
  ```bash
  curl -v https://example.com
  ```
  
  **Output:**
  Verbose logs + response body.
  
- Fetch only the HTTP headers without downloading the webpage body
  
  ```bash
  curl -I https://example.com
  ```
  
  **Output:**
  HTTP headers (status code, server info, etc.)
  
- Show full server response including headers and the response body
  
  ```bash
  curl -i https://example.com
  ```
  
  **Output:**
  HTTP headers + webpage content.

- Generate a detailed binary trace file for low-level debugging
  
  ```bash
  curl --trace curl.log https://example.com
  ```
  
  **Output:**
  A file `curl.log` with raw trace data.
  
- Generate a human-readable ASCII trace of the request and response
  
  ```bash
  curl --trace-ascii debug.txt https://example.com
  ```
  
  **Output:**
  Text-based debug log in `debug.txt`.

---

### Downloading & Uploading

- Upload a file to a server using multipart/form-data
  
  ```bash
  curl -F "file=@backup.tar.gz" https://example.com/upload
  ```
  
  **Output:**
  Server response indicating upload success/failure.
  
- Resume a partially downloaded file (continue from last saved position)
  
  ```bash
  curl -C - -O https://example.com/largefile.iso
  ```
  
  **Output:**
  Download continues without starting over.
  
  **Purpose:**
  Useful for large downloads and unstable internet links.

---

### Proxy Related

- Send your request through an HTTP proxy server
  
  ```bash
  curl -x http://proxy:8080 https://example.com
  ```
  
  **Output:**
  Content fetched through the proxy.
  
  **Purpose:**
  Used in corporate networks or restricted environments.

---

### Rate Limits / Timeout

- Cancel the request if it takes longer than the specified number of seconds
  
  ```bash
  curl --max-time 10 https://example.com
  ```
  
  **Output:**
  Timeout error if request exceeds **10 seconds**.
  
  **Purpose:**
  Prevents scripts from hanging.
  
- Download a file while limiting the maximum bandwidth usage
  
  ```bash
  curl --limit-rate 200k -O https://example.com/file.iso
  ```
  
  **Output:**
  File downloaded slowly at **200 KB/s**.
  
  **Purpose:**
  Avoids consuming too much bandwidth.

---

