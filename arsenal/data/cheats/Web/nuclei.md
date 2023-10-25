# Nuclei

% blackbox, cve

#plateform/linux #target/remote #cat/RECON #cat/ATTACK/EXPLOIT
## Nuclei - find Crit with reco
```
nuclei -u <url> -as -s critical
```

## Nuclei - find Crit with reco, multiple url
```
nuclei -l <targets_file> -as -s critical 
```

## Nuclei - find Crit and High with reco
```
nuclei -u <url> -as -s critical, high
```