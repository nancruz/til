# journalctl

Query the `systemd` journal

## Options
- `-u`: Displays the systemd journal for the given unit.

**Example**: `journalctl -u myservice`

- `-f`: Show only the most recent journal entries, and continuously print new entries as they are appended to the journal.

**Example**: `journalctl -u myservice -f`

- `-n`: Show and limit the most recent journal entries.

**Example**: `journalctl -u -n100`

