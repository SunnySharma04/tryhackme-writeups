# TryHackMe: Linux Fundamentals Part 1

## Room Summary

This room provides a foundational introduction to the Linux operating system, focusing on fundamental terminal commands, file system navigation, file manipulation, reading system documentation, and understanding basic directory structures essential for security operations and system administration.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Linux Fundamentals Part 1 |
| Difficulty | Very Easy |
| Topic | Linux CLI Basics, File System Navigation, Directory Structure, Basic Commands |
| Status | Completed |

## Skills Practiced

- Navigating the Linux hierarchical file system using absolute and relative paths
- Interacting with files and directories (creating, copying, moving, renaming, deleting)
- Viewing file contents using non-interactive and terminal-based viewing tools
- Utilizing command flags, inline options, and built-in help documentation (`man`, `--help`)
- Searching for specific files and directories using system utilities

## Hands-On & Command Reference

### File System Navigation & Directory Operations

```bash
# Print current working directory
pwd

# List contents with hidden files and detailed metadata
ls -la

# Change directory using absolute and relative paths
cd /var/log
cd ../..
cd ~

```

### File Creation, Inspection & Manipulation

```bash
# Create empty files and new directories
touch security_log.txt
mkdir -p ./investigation/artifacts

# Display file contents to terminal
cat security_log.txt

# Read large files page-by-page
less /var/log/syslog

# Display initial or trailing lines of a log file
head -n 20 /var/log/auth.log
tail -n 20 /var/log/auth.log

# Copy, move, and rename files
cp security_log.txt ./investigation/artifacts/
mv security_log.txt security_log_old.txt
rm security_log_old.txt

```

### System Help & File Searching

```bash
# Access manual pages for system commands
man ls

# Display concise flag documentation
grep --help

# Search for files by name across the filesystem
find / -name "config.txt" 2>/dev/null

```

## Tools and Platforms Learned

* TryHackMe
* Linux Terminal / Bash Shell
* Core Utilities (`ls`, `cd`, `cat`, `less`, `head`, `tail`, `cp`, `mv`, `rm`, `find`)

## Key Takeaways

* **Terminal Proficiency:** Mastering the command line is foundational for both offensive and defensive cybersecurity roles, as many security appliances and servers operate without a Graphical User Interface (GUI).
* **Log Inspection:** Commands like `head`, `tail`, and `less` are essential for efficiently inspecting large log files without overloading system memory.
* **Path Resolution:** Understanding the distinction between absolute paths (starting from `/`) and relative paths (starting from current directory) prevents navigation errors during terminal sessions.

## Defensive Learning

* Familiarity with standard Linux directory layouts (`/var/log`, `/etc`, `/tmp`) allows analysts to quickly spot out-of-place binary drops or unauthorized log tampering.
* Leverage `tail -f` when monitoring live system logs to observe real-time authorization attempts and potential brute-force activities.

```

```
