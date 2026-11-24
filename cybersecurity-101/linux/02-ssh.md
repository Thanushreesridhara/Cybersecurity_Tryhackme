# 02 - SSH

- **SSH (Secure Shell)** is a protocol that lets two devices talk to each other securely over a network.
- It encrypts everything in transit so nobody on the path can read it; the content is only revealed on the receiving machine.
- It lets you log in to remote computers, which is common on Linux because these machines often have no desktop and are used through the command line.
- It is a foundational tool across cybersecurity.

## What you need to connect

1. The IP address of the remote computer.
2. The username and password of an account on that computer.

## Command

```bash
ssh username@IPaddress
```
