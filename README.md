# Constructor

Constructor is a tool that can build up infrastructure in an automated way.

The main design goal of constructor was to have infrastructure specifications(blueprints) in code in a versioned manner.

## Setup

```sh
pip install constructor
```

Constructor works with environments, for this guide, we will create an environment called: dev

Log in to the AWS console.

Create a personal access key with Administrator privileges.

Run:

```sh
aws configure --profile dev
```

```sh
aws ec2 create-security-group --group-name web-server --profile dev --description 'Generic web server with SSH access'
aws ec2 authorize-security-group-ingress --group-name web-server --protocol tcp --cidr '0.0.0.0/0' --port 22 --profile=dev
aws ec2 authorize-security-group-ingress --group-name web-server --protocol tcp --cidr '0.0.0.0/0' --port 80 --profile=dev
aws ec2 authorize-security-group-ingress --group-name web-server --protocol tcp --cidr '0.0.0.0/0' --port 443 --profile=dev
```

```sh
mkdir ~/.constructor
aws ec2 create-key-pair --key-name dev --query 'KeyMaterial' --output text --profile dev > ~/.constructor/dev.pem
chmod 400 ~/.constructor/dev.pem
```

```sh
ssh-keygen -f ~/.constructor/id_rsa -t rsa -P ''
```

```sh
cat ~/.constructor/id_rsa.pub | pbcopy
```

Add ~/.constructor/id_rsa.pub to your git hosting.

Enter the credentials created in the earlier step.

Generate an SSH key pair, add the public key to your git hosting and put the private key(named id_rsa) into the ~/.constructor directory.