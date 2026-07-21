# `more` Command  

**Description:**  
The `more` command is a basic **terminal pager** used to view large text files **page by page**. It allows **forward navigation** and simple **searching** but lacks backward scrolling or advanced features available in modern pagers like `less`.  

## Options  

- `Space` – Move one full page down.  
- `Enter` – Move one line down.  
- `/keyword` – Search forward for a keyword within the file.  
- `n` – Jump to the next match after a search.  
- `+number` – Start viewing the file from a specific line number.  
- `+/pattern` – Start viewing from the first occurrence of a pattern.  
- `q` – Quit the `more` pager.  


## Examples  

- **View large files page by page** 
  ```bash
  more file.txt
  ```
  
  Move Down  
  - **Space**: Move one full page down.  
  - **Enter**: Move one line down.  


- **Search Inside File**  
  Search for text (only forward search).  
  ```
  /keyword
  ```
  **After search:**  
  - `n` → next match  
  
  **Limit:** Cannot search backward like `less`.  
  
- **Start Viewing from a Specific Line**  
  ```bash
  more +50 file.txt
  ```  
  **Output:** Opens file from line 50.  
  
  
- **Start Viewing from First Occurrence of a Pattern**  
  ```bash
  more +/ERROR /var/log/messages
  ```  
  **Output:** It will open the file from the very first error occurrence.  
  
  
- **Show Line Numbers**
   
  ```bash
  nl file.txt | more
  ```  
  Or  
  ```bash
  cat -n file.txt | more
  ```  
  >Note: `more` does not have built-in line numbers, but you can combine: 
  
- **Quit from `more` command**
  
  ```bash
  q
  ```  


## Real-Life Admin Scenarios  

- **Viewing config files quickly**  
  ```bash
  more /etc/passwd
  ```  

- **Searching logs for specific errors**  
  ```bash
  more +/timeout /var/log/messages
  ```
