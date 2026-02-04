# Archive CleanUp Tool 🚮

A lightweight, efficient Bash CLI utility designed to automate the cleanup of old backup archives. This tool scans the backup directory passed by the user, identifies compressed `.tar.gz` files older than 30 days, deletes them to save disk space, and maintains a detailed log history of all actions.

## ✨ Features

* **Smart Cleanup:** Automatically targets files with the `.tar.gz` extension.
* **Time-Based Rotation:** Only removes archives older than 30 days (mtime +30).
* **Automated Logging:** Maintains `archive-logs-history.log` within the target directory for audit trails.
* **Safety Checks:** Validates directory existence and input arguments before execution.
* **Global Access:** Designed to run as a system-wide command.

---

## 🚀 Installation

To use this tool globally from any directory, follow these steps:

1.  **Clone the script:**
    ```git
    git clone https://github.com/2Kelvin/archives-cleanup.git
    ```

2.  **Change into the directory**
    ```git
    cd archives-cleanup
    ```

3.  **Make the script executable**
    ```bash
    chmod +x cleanup-tool
    ```

3.  **Move script to global bin:**
    Move the script to `/usr/local/bin` to ensure it is available in your system `$PATH`.
    ```bash
    sudo mv cleanup-tool /usr/local/bin/cleanup-tool
    ```

---

## 🛠 Usage

Because this tool is installed in a protected system directory and often manages backups in restricted folders, it should be executed with **root privileges** or from a user with **sudo**.

To run the tool globally, use:

```bash
sudo cleanup-tool /path/to/your/backups
```

### Example
If you have backups stored in `/var/backups/my-logs-backup-folder`, simply run:

```bash
sudo cleanup-tool /var/backups/my-logs-backup-folder
```

<img width="1820" height="187" alt="Screenshot 2026-02-04 083318" src="https://github.com/user-attachments/assets/23fe2667-b706-4b80-a123-8b5bace45024" />


## 🤖 Automation Ready

This utility is designed for headless execution and is perfect for scheduled system maintenance. Since it is installed in `/usr/local/bin`, it can be easily integrated into your preferred scheduling engine; **systemmd timers** or **cron jobs**.

## 📝 Logging System

The tool maintains a continuous audit trail by creating or updating a log file named `archive-logs-history.log` directly within your target directory. 

### What is tracked:
* **Timestamps:** Precise records of when the cleanup was initiated.
* **Deletion Manifest:** A specific list of every `.tar.gz` filename removed during the session.
* **Status Reports:** Clear confirmation of "Success" or specific error codes if the process fails.

### Sample Log Entry:

```bash
cat /path/to/your/archive-logs-history.log
```

<img width="1807" height="376" alt="Screenshot 2026-02-04 084649" src="https://github.com/user-attachments/assets/15bc9a25-9744-4db1-8f93-ecdc5e34a547" />
