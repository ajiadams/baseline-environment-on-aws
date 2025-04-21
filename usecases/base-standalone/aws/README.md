# AWS CLI v2

This bundle contains a built executable of the AWS CLI v2.

## Installation

To install the AWS CLI v2, run the `install` script:

```
$ sudo ./install
You can now run: /usr/local/bin/aws --version
```

This will install the AWS CLI v2 at `/usr/local/bin/aws`. Assuming
`/usr/local/bin` is on your `PATH`, you can now run:

```
$ aws --version
```

### Installing without sudo

If you don't have `sudo` permissions or want to install the AWS
CLI v2 only for the current user, run the `install` script with the `-b`
and `-i` options:

```
$ ./install -i ~/.local/aws-cli -b ~/.local/bin
```

This will install the AWS CLI v2 in `~/.local/aws-cli` and create
symlinks for `aws` and `aws_completer` in `~/.local/bin`. For more
information about these options, run the `install` script with `-h`:

```
$ ./install -h
```

### Updating

If you run the `install` script and there is a previously installed version
of the AWS CLI v2, the script will error out. To update to the version included
in this bundle, run the `install` script with `--update`:

```
$ sudo ./install --update
```

### Removing the installation

To remove the AWS CLI v2, delete the its installation and symlinks:

```
$ sudo rm -rf /usr/local/aws-cli
$ sudo rm /usr/local/bin/aws
$ sudo rm /usr/local/bin/aws_completer
```

Note if you installed the AWS CLI v2 using the `-b` or `-i` options, you will
need to remove the installation and the symlinks in the directories you
specified.

## Deploy

### standalone に移動して yarn

```bash
$ cd usecases/base-standalone/
$ yarn install
```

### 有効な Stack の確認

```bash
$ npx cdk ls -c environment=dev
BLEA-BASE-Guardduty
BLEA-BASE-SecurityHub
BLEA-BASE-Trail
BLEA-BASE-SecurityAlarm
BLEA-BASE-Iam
BLEA-BASE-Config
BLEA-BASE-ConfigCtGuardrail
BLEA-BASE-ConfigRule
BLEA-BASE-ChatbotSecurity # 不要
```

## 各 Stack の deploy

### BLEA-BASE-Guardduty

おそらくすでに設定済みでエラーになるため実行不要

```bash
$ # yarn cdk deploy BLEA-BASE-Guardduty -c environment=dev
```

### BLEA-BASE-SecurityHub

```bash
$ yarn cdk deploy BLEA-BASE-SecurityHub -c environment=dev
BLEA-BASE-SecurityHub: creating CloudFormation changeset...
 ✅  BLEA-BASE-SecurityHub

✨  Deployment time: 19.84s

Stack ARN:
arn:aws:cloudformation:ap-northeast-1:207898528713:stack/BLEA-BASE-SecurityHub/edac90a0-e5b7-11ef-910f-0662ddb229f1

✨  Total time: 27.91s
```

### BLEA-BASE-Trail

```bash
$ yarn cdk deploy BLEA-BASE-Trail -c environment=dev
BLEA-BASE-Trail: creating CloudFormation changeset...
 ✅  BLEA-BASE-Trail

✨  Deployment time: 78.73s

Outputs:
BLEA-BASE-Trail.ExportsOutputRefCloudTrailLogGroup343A29D62364BB0C = BLEA-BASE-Trail-CloudTrailLogGroup343A29D6-1N3UvQCIjO2N
Stack ARN:
arn:aws:cloudformation:ap-northeast-1:207898528713:stack/BLEA-BASE-Trail/431668e0-e5b8-11ef-b46c-06d64fd9cbf7

✨  Total time: 86.24s
```

### BLEA-BASE-SecurityAlarm

```bash
$ yarn cdk deploy BLEA-BASE-SecurityAlarm -c environment=dev
BLEA-BASE-SecurityAlarm: creating CloudFormation changeset...

 ✅  BLEA-BASE-SecurityAlarm

✨  Deployment time: 78.24s

Outputs:
BLEA-BASE-SecurityAlarm.ExportsOutputRefSecurityAlarmTopicEE71C63385BAAF8E = arn:aws:sns:ap-northeast-1:207898528713:BLEA-BASE-SecurityAlarm-SecurityAlarmTopicEE71C633-PkBdAjOVOWrh
Stack ARN:
arn:aws:cloudformation:ap-northeast-1:207898528713:stack/BLEA-BASE-SecurityAlarm/c77bfeb0-e5b8-11ef-a78a-0678de8972a3

✨  Total time: 85.84s
```

### BLEA-BASE-Iam

```bash
$ yarn cdk deploy BLEA-BASE-Iam -c environment=dev
BLEA-BASE-Iam: creating CloudFormation changeset...
 ✅  BLEA-BASE-Iam

✨  Deployment time: 62.81s

Stack ARN:
arn:aws:cloudformation:ap-northeast-1:207898528713:stack/BLEA-BASE-Iam/1bc2b3b0-e5b9-11ef-ae28-06b080456a87

✨  Total time: 70.36s
```

### BLEA-BASE-Config

```bash
$ yarn cdk deploy BLEA-BASE-Config -c environment=dev
BLEA-BASE-Config: creating CloudFormation changeset...
 ✅  BLEA-BASE-Config

✨  Deployment time: 41.54s

Stack ARN:
arn:aws:cloudformation:ap-northeast-1:207898528713:stack/BLEA-BASE-Config/85f34d80-e5b9-11ef-9f00-0eb9c9510769

✨  Total time: 48.5s
```

### BLEA-BASE-ConfigCtGuardrail

```bash
$ yarn cdk deploy BLEA-BASE-ConfigCtGuardrail -c environment=dev
BLEA-BASE-ConfigCtGuardrail: creating CloudFormation changeset...
 ✅  BLEA-BASE-ConfigCtGuardrail

✨  Deployment time: 14.43s

Stack ARN:
arn:aws:cloudformation:ap-northeast-1:207898528713:stack/BLEA-BASE-ConfigCtGuardrail/c3a69740-e5b9-11ef-a282-0a46fecfe2b9

✨  Total time: 22.68s
```

### BLEA-BASE-ConfigRule

```bash
$ yarn cdk deploy BLEA-BASE-ConfigRule -c environment=dev
BLEA-BASE-ConfigRule: creating CloudFormation changeset...
 ✅  BLEA-BASE-ConfigRule

✨  Deployment time: 51.75s

Stack ARN:
arn:aws:cloudformation:ap-northeast-1:207898528713:stack/BLEA-BASE-ConfigRule/08c487b0-e5ba-11ef-b8fc-06871511632d

✨  Total time: 59.45s
```
