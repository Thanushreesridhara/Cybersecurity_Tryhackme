# 01 - Linux Basics

## Core commands

| Command | What it does | Example |
|---------|--------------|---------|
| `whoami` | Shows which user you are on the system | `whoami` |
| `echo` | Outputs the text you give it | `echo hello` |
| `ls` | Lists what is in the current folder | `ls` |
| `ls -a` | Lists all files, including hidden ones | `ls -a` |
| `cd` | Changes directory (moves into a folder) | `cd /etc` |
| `cd /home/<user>` | Goes back to your home directory (`cd ~` also works) | `cd ~` |
| `cat` | Shows the contents of a file | `cat notes.txt` |
| `pwd` | Prints the working directory ("where am I?") | `pwd` |
| `find` | Searches for files by name | `find -name passwords.txt` |
| `grep` | Searches for text inside a file | `grep "password123" passwords.txt` |
| `--help` | Lists a command's options with a short description and example | `ls --help` |

## File and folder management

| Command | Full name | Purpose |
|---------|-----------|---------|
| `touch` | touch | Create a file |
| `mkdir` | make directory | Create a folder |
| `cp` | copy | Copy a file or folder |
| `mv` | move | Move (or rename) a file or folder |
| `rm` | remove | Remove a file or folder |

## Operators

| Operator | What it does |
|----------|--------------|
| `&` | Runs the command in the background, so you can keep working while it runs |
| `&&` | Runs two commands in order; the second starts only after the first succeeds |
| `>` | Redirects output into a file and **overwrites** what was there |
| `>>` | Redirects output into a file and **appends** to the bottom |

## Filesystem tree

- `/` is the trunk (the **root** of the filesystem); directories like `/etc`, `/var` and `/home` are branches, and files are leaves.
- "Root" can also mean the top-level directory of a project, so `/` (filesystem root) is not the same thing as a project root.
- `/etc`: system and program configuration files, e.g. `sudoers`, which lists the users and groups allowed to run commands with `sudo`.
- `/var`: variable data that services and applications read or write often, such as logs in `/var/log` and databases.
- `/root`: the home directory of the `root` system user, separate from `/home` where regular users live.
- `/tmp`: temporary storage for data needed only once or twice; cleared on reboot.

## Switching users: `su -l`

- `su -l` (same as `su -` or `su --login`) switches to another user with a full login shell, e.g. `su -l` (root) or `su -l user2`.
- It loads the target user's own environment (`HOME`, `PATH`, shell startup files) instead of keeping yours.
- It moves you into the target user's home directory, such as `/root` for root.
- Plain `su` switches the user but keeps your current environment and directory, which can cause confusing behaviour.
- It asks for the **target** user's password, whereas `sudo` asks for your own.
