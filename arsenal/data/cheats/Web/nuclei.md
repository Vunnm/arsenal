# Nuclei

% blackbox, cve

#plateform/linux #target/remote #cat/RECON #cat/ATTACK/EXPLOIT
## Nuclei
```
nuclei -u <url>
```

## Nuclei - find Crit with reco
```
nuclei -u <url> -as -s critical
```

## Nuclei - find Crit and High with reco
```
nuclei -u <url> -as -s critical, high
```

## Nuclei - private interactsh
```
nuclei -u <url> -iserver <interactsh> -itoken <token_ish>
```