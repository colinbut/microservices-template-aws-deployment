# Microservices Template AWS Deployment

Deployment for Microservices Template application on AWS infrastructure

### Technologies

- Ansible

### Pre-requisites

Make sure you have provisioned the EC2 instances on AWS by following along the https://github.com/colinbut/microservices-template-aws-env-setup

### Setup/Configuration

In the ansible inventory file (`hosts`) you will require to put in the correct public IP addresses of your provisioned EC2 instances.

e.g.

```
webserver01 ansible_host=3.8.126.49
webserver02 ansible_host=3.8.174.149
webserver03 ansible_host=35.178.148.106
```

Also...

In the `ansible.cfg` (ansible configuration) file you need to change the location of where the "private_key_file" property points to:
```
private_key_file =  ~/dev/aws/MyLondonKP.pem
```

for instance, I have mine (MyLondonKP.pem) already setup under `/dev/aws` directory under my root directory.

### Deploy

```bash
ansible-playbook -i hosts deploy_app.yml
```

This will deploy the app (by copying i.e. scp) to the EC2 instances.
note* - due to network latencies this ansible task within might take a very long time to complete

### Start

```bash
ansible-playbook -i hosts start_app.yml
```

### Comments

1. This assumes prior Ansible knowledge.
2. Feel free to fork this repo or copy contents of this repo and use as your reference
3. Feel free to change the Ansible deployment scripts as per your needs

### Maintainer
Colin But (colin.but@outlook.com)
