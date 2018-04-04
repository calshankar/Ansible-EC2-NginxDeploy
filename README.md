# Ansible Playbook using Dynamic Inventory
=========================================

This playbook can be used to deploy EC2 instance & deploying Nginx App which can be customized using Jinja2 template engine.

The inventory file is generated by EC2 dynamic inventory script, which generates your current running infrastructure on the cloud as dynamic inventory file based on custom tags included as part of boot strapping the EC2 instance.

Primarily, the playbook that you just ran is combination of two roles, namely:

- aws_ec2: This role creates security group, opens up ports & boot strap the instance (default: t2.micro). The instance type & number of instance can be changed here

- nginx_web: This role provisions the nginx web server, jinja2 template with dynamic variable which sets-up the page, besides the option (you will be prompted) to terminate the instances (optional)

## Requirements

To run this playbook on your local machine, you must install the following prerequisites:

- Ansible 2.4 or higher
- Python PIP package manager
- The following PIP packages:
  - awscli
  - boto/boto3

You must also configure your local environment with your AWS credentials and you will also need to export AWS_DEFAULT_PROFILE, AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY to your shell env.

### macOS Environments

On macOS environments it is recommended that you use the Homebrew package manager to install the most recent version of Python 2.7.

See [brew.sh](http://brew.sh) for details on how to install Homebrew.

Once Homebrew is installed you can install the latest version of Python 2.7 as follows:

```bash
$ brew install python2

```

This will install the PIP package manager as `pip2` and you can install Ansible and required dependencies:

```bash
$ pip2 install ansible awscli boto3

```

Note that `boto3` must also be installed in the system python, which you can perform as follows:

```bash
$ sudo -H /usr/bin/python -m easy_install pip

$ sudo -H /usr/bin/python -m pip install boto3 --ignore-installed six

```

Once you have installed `boto3` in your system python, it is recommended to run the following commands to ensure your Homebrew and system python environments are configured correctly:

```
$ brew unlink python

$ brew link --overwrite python

```

## Role Variables

Check the group_vars folder & the respective roles folders. Following are the variables under `group_vars/all/vars.yml` which can be modified and referenced in the tasks.

- instance_type: t2.micro
- instance_region: ap-south-1
- ami_id: ami-e60e5a89

Any custom variable to be used in roles can be added here

## Dependencies

Dependant on the role `aws_ec2` for creating the instance. You control the run of the role by using by the tag/skip tags `setup`. This role can also be adopted for any environment by changing the hostvars of the role accordingly.

Dependant on the role `nginx_web` which provisions the nginx web server. You control the run of the role by using by the tag/skip tags `deploy`

`site.yml` master file drives both the roles

## Getting Started

To run the playbook, you just need to run the master file site.yml which executes the role based on the tags specified

```
ansible-playbook site.yml --skip-tags terminate
```

This command with skip the tasks for terminating the instance, although you can run without it because you will be prompted before the playbook starts terminating the instance

## License
-------

BSD

## Author Information
------------------

by [Shankar Ramanathan](https://linkedin.com/in/shankar-ramanathan-a5715b9/)
