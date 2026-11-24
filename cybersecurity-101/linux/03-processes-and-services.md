# 03 - Processes and Services

## What is a process?

- A process is a program running on the machine, managed by the kernel.
- Every process gets a **PID** (process ID), assigned in the order the processes start.

## Viewing processes

| Command | What it does |
|---------|--------------|
| `ps` | Lists the processes in your own session, with status, CPU time and command |
| `ps aux` | Lists all processes, including other users' and system processes |
| `ps aux \| grep <name>` | Filters the list for a specific process |
| `top` | Live, refreshing statistics for running processes |

## Managing processes: `kill`

- `kill <PID>` terminates a process, e.g. `kill 1337`.

| Signal | Effect |
|--------|--------|
| `SIGTERM` | Kills the process but lets it clean up first |
| `SIGKILL` | Kills the process immediately, with no cleanup |
| `SIGSTOP` | Stops (suspends) the process |

## How processes start

- **Namespaces** split the system's resources (CPU, RAM, priority) into slices and isolate processes from each other; only processes in the same namespace can see each other, which helps security.
- `systemd` is the init process started at boot (it is **PID 1**), and every program you start runs as a child process of it.
- Services such as web servers, database servers and file transfer servers are often set to start at boot.

## `systemctl`

- Format: `systemctl [option] [service]`, e.g. `systemctl start apache2`.

| Option | Effect |
|--------|--------|
| `start` | Starts the service now |
| `stop` | Stops the service |
| `enable` | Starts the service automatically at boot |
| `disable` | Stops it from starting at boot |
| `status` | Shows whether the service is running |

## Foreground and background processes

- **Foreground:** the process owns your terminal; you can't run other commands until it finishes, and its output is shown directly.
- **Background:** the process runs behind the scenes and you get your prompt back, so you can keep working.

| Action | How |
|--------|-----|
| Start a command in the background | `command &` (prints the job number and PID instead of the output) |
| Pause a foreground process | `Ctrl + Z` (it is paused until resumed) |
| Resume a paused process in the background | `bg` |
| Bring a background or paused process back to the foreground | `fg` |
| List background jobs | `jobs` |

```bash
sleep 60      # foreground: terminal is blocked for 60 seconds
sleep 60 &    # background: prompt returns immediately
jobs          # shows the background job
fg            # brings it back to the foreground
```

- Backgrounding is useful for long tasks like copying big files or running scripts.
