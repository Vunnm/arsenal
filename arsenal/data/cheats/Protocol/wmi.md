# WMI

## NetExec - Lister les sessions de delegation de jetons

```
nxc wmi win_ip.txt -u <user> -p <password> --wmi "SELECT LogonId, Name, StartTime, LogonType FROM Win32_LogonSession WHERE LogonType = 9"
```

## Powershell - Lister les sessions de delegation de jetons

```
Get-WmiObject -Query "SELECT LogonId, Name, StartTime, LogonType FROM Win32_LogonSession WHERE LogonType = 9" | Select-Object LogonId, Name, StartTime, LogonType | Format-Table -AutoSize
```