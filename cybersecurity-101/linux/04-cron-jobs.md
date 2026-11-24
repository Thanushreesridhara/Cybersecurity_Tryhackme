# 04 - Scheduling Tasks with Cron

- `cron` is a process started at boot that runs scheduled tasks (cron jobs).
- You manage cron jobs through **crontabs**.
- Typical uses: running commands, backing up files, or launching programs after the system has booted.

## Editing the crontab

- `crontab -e` opens your crontab in an editor of your choice (e.g. Nano).
- `crontab -l` lists your current cron jobs.

## Format

```
* * * * * command
| | | | |
| | | | +-- day of week (0-7)
| | | +---- month (1-12)
| | +------ day of month (1-31)
| +-------- hour (0-23)
+---------- minute (0-59)
```

- The `*` wildcard means "any value": use it for fields you don't care about.

## Example: back up a folder every 12 hours

```
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```

- `0` runs at minute 0.
- `*/12` runs every 12 hours (00:00 and 12:00).
- The remaining `*` fields mean every day, every month, every day of the week.
- `cp -R` copies the Documents folder recursively into `/var/backups/`.

## Helpful tools

- [Crontab Generator](https://crontab-generator.org/): builds the schedule format for you.
- [Cron Guru](https://crontab.guru/): explains a schedule in plain English.
