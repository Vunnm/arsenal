# gobuster

% fuzzer, fuzz, gobuster

#plateform/linux #target/remote #cat/ATTACK/FUZZ
## gobuster scan classic
```
gobuster dir -u <url> -w <wordlist>
```

## gobuster scan pentest classic fuzz
```
gobuster dir -u <url> -w <wordlist> -x json,html,php,txt,xml,md
```

## gobuster scan high rate
```
gobuster dir -u <url> -w <wordlist> -t 30
```

## gobuster scan with adding extension
```
gobuster dir -u <url> -w <wordlist> -x json,html,php,txt
```

# ffuf

% fuzzer, fuzz, ffuf
#plateform/linux #target/remote #cat/ATTACK/FUZZ
## ffuf fuzz keyword in url
```
ffuf -w <wordlist> -u <url>/FUZZ -ac
```

## ffuf multiple url and store res
```
for i in `cat <urls>`; do ffuf -w <wordlist> -u https://$i/FUZZ -ac -o $i.html -of html; done
```

## ffuf fuzz url with header
```
ffuf -w <wordlist> -u <url>/FUZZ -ac -H '<header>'
```

## ffuf fuzz Host filter response size
```
ffuf -w <wordlist> -u <url> -H "Host: FUZZ" -fs <response_size>
```

## ffuf GET parameter fuzzing
```
ffuf -w <wordlist> -u <url>?<param>=FUZZ -fs <response_size>
```

## ffuf POST parameter fuzzing and filter response code 401
```
ffuf -w <wordlist> -u <url> -X POST -d "username=admin\&password=FUZZ" -fc 401
```

= wordlist: /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt