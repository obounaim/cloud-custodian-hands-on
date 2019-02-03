# Cloud Custodian Hands-on

## Prerequisites
1. AWS account 
2. [AWS Access Key ID and Secret Key](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)
3. python2
4. virtualenv and pip
5. [IAM role for AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html) with "AdministratorAccess" policy attached

## Install Cloud Custodian and create CloudTrail Trail

### 1. Clone git repository

```bash
git clone git@github.com:obounaim/cloud-custodian-hands-on.git
cd cloud-custodian-hands-on
```

### 2. Create Cloud Custodian virtual environment 

```bash
virtualenv -p /usr/bin/python2 c7n_venv
source c7n_venv/bin/activate
pip install c7n
```

### 3. Create CloudTrail Trail and save it to an S3 bucket 

[AWS documentation](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-a-trail-using-the-console-first-time.html)

## Cloud Custodian basic commands

### Get Cloud Custodian command help

```bash
custodian --help
custodian run --help
```

### Get Cloud Custodian schema 

Example with ec2 resource :

```bash
custodian schema aws.ec2 
custodian schema aws.ec2.actions
custodian schema aws.ec2.filters 
```

### Deploy/Run Cloud Custodian policy 

```bash
custodian run policy.yml --output-dir logs/
custodian run policy.yml --output-dir logs/ --profile aws_dev_account
```

### Disable Cloud Custodian cache

```bash
custodian run policy.yml --output-dir logs/ --cache-period 0
```

## Hands-On

Policy examples in "examples" folder :

```bash
cd examples
mkdir logs
```

### 1. Basic mode policy

```bash
basic_mode.yml
```

### 2. CloudTrail mode policy 

```bash
cloudtrail_mode.yml
```

### 3. Periodic mode policy 

```bash
periodic_mode.yml
```

### 4. **Disable/Delete CloudTrail Trail and all other resources**

