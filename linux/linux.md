# Commands
   - cls/clear
   - ls
   - dir
   - mkdir
   - rmdir /s /q file/foldername

# 1. File and Directory Management
| Task             | Linux Command    | Windows Command (CMD/PowerShell)               |
|------------------| ---------------- | ---------------------------------------------- |
| **List files**   | `ls`             | `dir`                                          |
| ****Change directory**** | `cd`             | `cd`                                           |
| ****Copy file****        | `cp source dest` | `copy source dest` or `Copy-Item` (PowerShell) |
| ****Move/Rename file**** | `mv old new`     | `move old new` or `Rename-Item` (PowerShell)   |
| ****Delete file****      | `rm filename`    | `del filename` or `Remove-Item` (PowerShell)   |
| ****Create directory**** | `mkdir dirname`  | `mkdir dirname`                                |



# 2. User and Permission Management

| Task                    | Linux Command | Windows Command (CMD/PowerShell) |
| ----------------------- | ------------- | -------------------------------- |
| **Change file permissions** | `chmod`       | `icacls`                         |
| **Change file owner**       | `chown`       | `takeown` and `icacls`           |
| **Switch user**             | `su` / `sudo` | `runas`                          |
| **View current user**       | `whoami`      | `whoami`                         |



# 3. System Monitoring and Process Management
   | Task                   | Linux Command         | Windows Command (CMD/PowerShell)                |
   | ---------------------- | --------------------- | ----------------------------------------------- |
   | **Show running processes** | `ps` / `top` / `htop` | `tasklist` / `Get-Process` (PowerShell)         |
   | **Kill a process**         | `kill PID`            | `taskkill /PID PID`                             |
   | **System uptime**          | `uptime`              | `net statistics workstation`                    |
   | **View memory usage**      | `free -h` / `top`     | `systeminfo` or `Get-ComputerInfo` (PowerShell) |


# 4. Networking
   | Task                  | Linux Command       | Windows Command (CMD/PowerShell) |
   | --------------------- | ------------------- | -------------------------------- |
   | **Check network config**  | `ifconfig` / `ip a` | `ipconfig`                       |
   | **Ping a host**           | `ping host`         | `ping host`                      |
   | **Display routing table** | `netstat -rn`       | `route print`                    |
   | **Show open ports**       | `netstat -tuln`     | `netstat -an`                    |
   | **Test connectivity**     | `traceroute host`   | `tracert host`                   |



# 5. Package and Software Management
   | Task              | Linux Command                         | Windows Command (CMD/PowerShell)                                  |
   | ----------------- | ------------------------------------- | ----------------------------------------------------------------- |
   | **Install a package** | `apt install pkg` / `yum install pkg` | `winget install pkg` or `choco install pkg` (if using Chocolatey) |
   | **Update packages**   | `apt update && apt upgrade`           | `winget upgrade` / `choco upgrade`                                |
   | **Remove a package**  | `apt remove pkg`                      | `winget uninstall pkg` / `choco uninstall pkg`                    |
