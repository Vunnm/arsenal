# ldap

#plateform/linux  #target/remote  #protocol/ldap  #port/639 #port/389

## ldap nmap
#cat/RECON 
```
nmap -n -sV --script "ldap* and not brute" -p 389 <ip>
```

## ldapsearch base
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -s base
```

## ldapsearch SPN
#cat/ATTACK/CONNECT 
```
ldapsearch -Y GSSAPI -H ldap://<dc_fqdn> -D "<user>" -W -b "dc=<domain>,dc=<path>" "servicePrincipalName=*" servicePrincipalName
```
	
## ldapsearch with base dn
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -b <basedn>
```

## ldapsearch base with authentication
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -D <user>@<domain> -w '<password>' -b 'DC=<domain>,DC=<path>'
```

## ldapsearch - list all users
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -D <user>@<domain> -w '<password>' -b 'DC=<domain>,DC=<path>' '(&(objectCategory=person)(objectClass=user))'
```

## ldapsearch - list all users protected by adminCount
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -D <user>@<domain> -w '<password>' -b 'DC=<domain>,DC=<path>' '(&(objectCategory=user)(adminCount=1))'
```

## ldapsearch - list protected users
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -D <user>@<domain> -w '<password>' -b 'CN=Protected Users,CN=Users,DC=luisina,DC=fr' member
```

## ldapsearch - list all users with password, pass, identifiant or pwd in their description
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -D <user>@<domain> -w '<password>' -b 'DC=<domain>,DC=<path>' '(&(objectCategory=user)(|(description=*pass*)(description=*password*)(description=*identifiant*)(description=*pwd*)))'
```

## ldapsearch - list all computer with laps enabled and corresponding laps password if able
#cat/ATTACK/CONNECT 
```
ldapsearch -x -H ldap://<dc_fqdn> -D <user>@<domain> -w '<password>' -b 'DC=<domain>,DC=<path>' '(ms-Mcs-AdmPwdExpirationtime=*)' ms-Mcs-AdmPwd
```

## ldapdomaindump
#cat/ATTACK/CONNECT 
```
ldapdomaindump -o ldap_dump <dc-ip> -u '<domain_no_end>\<user>' -p '<password>' -at SIMPLE
```

## ldapsearch-ad - list all password policies including FGPP
#cat/ATTACK/CONNECT 
```
ldapsearch-ad.py --server '<dc_fqdn>' -d <domain> -u <user> -p <password> --type pass-pols
```

## ldapsearch-ad - get the FGPP applied to a group
#cat/ATTACK/CONNECT 
```
ldapsearch-ad.py --server '<dc_fqdn>' -d <domain> -u <user> -p <password> -t search -s '(samaccountname=<groupname>)' cn msDS-PSOApplied 
```

## ldapsearch-ad - get the FGPP applied to a user
#cat/ATTACK/CONNECT 
```
ldapsearch-ad.py --server '<dc_fqdn>' -d <domain> -u <user> -p <password> --type show-user -s '(samaccountname=<user>)'
```
