# Localstack up and running for aws-cli and terraform

## Introduction
[Localstack](https://www.localstack.cloud/) is a tool which emulates aws api locally on PC.
This project help setting up localstack up and running to use with terraform and aws-cli.
You can find localstack documentation [here](https://docs.localstack.cloud/overview/)

## Install prerequistes
- [Install docker if not already installed](https://docs.docker.com/engine/install/) - mandatory for our localstack install process!
- [Install aws-cli if not already installed](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) - can be installed after deployed localstack
- [Install terraform if not already installed](https://developer.hashicorp.com/terraform/install) - Optional

## Setup localstack
Clone this repository. It contains:
- docker-compose.yml file to launch localstack as container
- aws-localstack.env file with all aws environment variables configured to use localstack instead of aws account
```shell
git clone https://github.com/iNgk42/localstack-aws-terraform && cd localstack-aws-terraform
```

Launch localstack with docker compose file
```shell
docker compose up -d
```

Configure aws-cli to use localstack as endpoint
```shell
source aws-localstack.env
```

Now if you use either aws-cli or terraform to interact with aws api, it will talk to localstack.
``` shell
# create s3 bucket
aws s3 mb s3://my-localstack-bucket

# list s3 buckets
aws s3 ls
```
