# smb
% smb, samba

## nbtscan - scan network looking for hosts
#plateform/linux #target/remote #port/445 #protocol/smb #cat/RECON 
```
nbtscan -r <ip_range>
```

## smbclient with username and password
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/CONNECT  
```
smbclient \\\\<ip>\\<share> -U "<user>%<password>"
```

## smbclient sessions without password
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/CONNECT  
```
smbclient \\\\<ip>\\<share> -U "<user>%"
```

## smbclient null session
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/CONNECT  
```
smbclient \\\\<ip>\\<share> -U "%"
```

## smb - find not signed  smb
#plateform/linux #target/remote #port/445 #protocol/smb #cat/RECON 
```
nmap -Pn -sS -T4 --open --script smb-security-mode -p445 <ip>
```

## smb mount folder
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/CONNECT  
```
mount -t cifs //<ip>/<share> /tmp/mnttarget/ -o username=<user>,password=<pass>,domain=<domain>,uid=1000,gid=1000
```

## smb anonymous mount
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/CONNECT  
```
mount -t cifs //<ip>/<share> /tmp/mnttarget/ -o guest,uid=1000,gid=1000
```