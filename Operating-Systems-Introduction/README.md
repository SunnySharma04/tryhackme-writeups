# TryHackMe: Operating Systems: Introduction

## Room Summary

This room covers the core architecture, functions, and landscapes of operating systems. It explores kernel resource arbitration ("The Invisible Manager"), process scheduling, memory allocation, storage control, and user interaction modes (CLI vs. GUI) across modern platforms.

## Room Details

| Field | Details |
|---|---|
| Platform | TryHackMe |
| Room | Operating Systems: Introduction |
| Difficulty | Very Easy / Info |
| Topic | OS Architecture, Kernel Operations, Resource Management, CLI/GUI |
| Status | Completed |

## Skills Practiced

- Understanding core operating system architecture and kernel-space separation
- Analyzing kernel resource management (CPU, Memory, Storage, Devices)
- Differentiating process scheduling mechanisms and memory address space isolation
- Evaluating Command-Line Interfaces (CLI) vs. Graphical User Interfaces (GUI)
- Mapping operating system landscapes across Windows, Linux, and macOS environments

## Tools and Platforms Learned

- TryHackMe
- Operating System Management Shells (Bash, PowerShell)
- System Resource Monitoring Utilities
- System Architecture Models

## Key Takeaways

- The kernel serves as the central manager, safely arbitrating hardware access for unprivileged user processes.
- Memory isolation prevents running processes from reading or overwriting memory allocated to other applications.
- Command-Line Interfaces (CLI) provide the scriptability and low-overhead control required for security administration.
- System security relies heavily on enforcing strict user-space vs. kernel-space protection boundaries.

## Defensive Learning

- Enforce kernel protection features like ASLR and DEP/NX to mitigate memory corruption vulnerabilities.
- Implement least privilege access controls across CLI shells and administrative utilities.
- Audit driver installations and process creation events using centralized logging.
- Limit unnecessary background services to reduce system attack surface.
