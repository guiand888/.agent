# Mikrotik SSH Command Execution Standards

## Purpose
Define secure and reliable SSH command execution patterns for Mikrotik RouterOS devices.

## Scope
All Mikrotik device interactions via SSH, including single commands, command sequences, and script execution.

## Rules

### Always
- Use SSH for connections: `ssh [username]@[device_ip] "[command]"`
- Enclose Mikrotik commands in quotes when using SSH
- Use variables or parameters instead of hardcoding IPs or usernames
- Verify command success by checking the output
- Check command output for errors after execution
- Backup configuration with `export` before making changes

### Never
- Execute unquoted commands that may be misinterpreted by shell
- Hardcode credentials or device IPs in commands
- Assume command success without output verification

### Ask Before
- Running commands that could disrupt network connectivity
- Executing scripts without prior review
