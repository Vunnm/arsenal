# nmap

#plateform/linux #target/remote #cat/RECON #tag/scan

## nmap - hosts alive
```
nmap -sn <ip_range>
```

## nmap - classic scan + save
```
nmap -sC -sV <ip> -oA <output_file>
```

## nmap - read targets from a file
```
nmap -sC -sV -iL <targets_file>
```

## nmap - full port + save
```
nmap -p- -sC -sV -oA <output_file> <ip>
```

## nmap - quick scan top ports 100
```
nmap --top-ports 100 --open -sV <ip>
```

## nmap - big top ports 5000
```
nmap --top-ports 5000 --open -sV <ip>
```

## nmap - full port
```
nmap -p- -sV <ip>
```

## nmap - host with a given port
```
nmap <ip> -p<port_list> --open
```

## nmap - FULL
```
IP=<ip>;
ports=$(nmap -p- --min-rate=1000 -n -T4 $IP | grep ^[0-9] | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//);
nmap -Pn -sC -sV -p$ports $IP -oN scan.txt --reason --script=vuln
```

## nmap - udp scan
```
nmap -sU <ip>
```

## nmap - low rate Classic
```
nmap --max-rate 100 -sC -sV <ip>
```

## massscan - full port
```
masscan -p 1-65535 <ip> -e <dev> --rate=1000
```

