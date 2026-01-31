Linux Architecture, Processes, and systemd

1. Core Components

The Kernel: The central core. It manages hardware (CPU, Memory, Disks) and prevents applications from crashing the entire system.

User Space: The environment where all user applications (like your shell, Docker, or web browsers) run. It communicates with the Kernel via System Calls.

Init System (systemd): The first process to start (PID 1). It is the "mother of all processes," responsible for starting and managing services.

2. Process Management
Processes are instances of running programs. They are usually created through a Fork/Exec model: a parent process copies itself (fork) and then replaces that copy with a new program (exec).

Process States:
Running (R): Actively using the CPU or ready to run.

Sleeping (S): Waiting for an event (like user input) to wake up.

Uninterruptible Sleep (D): Usually waiting for Disk I/O; cannot be killed until the hardware responds.

Stopped (T): Suspended by a user or debugger (e.g., via Ctrl+Z).

Zombie (Z): A completed process whose entry remains in the process table because the parent hasn't acknowledged its exit.

3. Why systemd Matters
systemd is the standard manager for modern Linux. It’s crucial because:
It starts services in parallel, making boot times faster.
It uses Unit Files (.service) to define how apps should behave.
It automatically restarts failed services, which is vital for high availability.
It centralizes logs via the systemd-journald service.

4. Daily DevOps Toolkit
top: Real-time view of system resource usage.
ps aux: Snapshot of all running processes and their states.
systemctl status <service>: Check if a background service is healthy.
journalctl -xe: View the most recent system logs to debug failures.
kill -9 <PID>: Send a "SIGKILL" signal to force-stop a hung process.

