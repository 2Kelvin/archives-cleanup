# Archive CleanUp Tool 🚮

A lightweight, efficient Bash CLI utility designed to automate the cleanup of old backup archives. This tool scans a specified directory, identifies compressed `.tar.gz` files older than 30 days, deletes them to save disk space, and maintains a detailed log history of all actions.

## ✨ Features

* **Smart Cleanup:** Automatically targets files with the `.tar.gz` extension.
* **Time-Based Rotation:** Only removes archives older than 3 days (mtime +3).
* **Automated Logging:** Maintains `archive-logs-history.log` within the target directory for audit trails.
* **Safety Checks:** Validates directory existence and input arguments before execution.
* **Global Access:** Designed to run as a system-wide command.

---

## 🚀 Installation

To use this tool globally from any directory, follow these steps:

1.  **Clone or create the script:**
    ```bash
    nano archive-purge
    ```
    *(Paste the script code into the file and save)*

2.  **Make the script executable:**
    ```bash
    chmod +x archive-purge
    ```

3.  **Move to global bin:**
    Move the script to `/usr/local/bin` to ensure it is available in your system `$PATH`.
    ```bash
    sudo mv archive-purge /usr/local/bin/archive-purge
    ```

---

## 🛠 Usage

Because this tool is installed in a protected system directory and often manages backups in restricted folders, it should be executed with **root privileges**.

To run the tool globally, use:

```bash
sudo archive-purge /path/to/your/backups
```

### Example
If you have backups stored in `/var/backups/app-data`, simply run:

```bash
archive-purge /var/backups/app-data
```

## 🤖 Automation Ready

This utility is designed for headless execution and is perfect for scheduled system maintenance. Since it is installed in `/usr/local/bin`, it can be easily integrated into your preferred scheduling engine, **systemmd timers** or **cron jobs**.

## 📝 Logging System

The tool maintains a continuous audit trail by creating or updating a log file named `archive-logs-history.log` directly within your target directory. 



### What is tracked:
* **Timestamps:** Precise records of when the cleanup was initiated.
* **Deletion Manifest:** A specific list of every `.tar.gz` filename removed during the session.
* **Status Reports:** Clear confirmation of "Success" or specific error codes if the process fails.

### Sample Log Entry:

add screenshot here