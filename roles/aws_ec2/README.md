Role Name
=========

Creating security group & launching EC2 instance

Requirements
------------

To run this playbook on your local machine, you must install the following prerequisites:

- Ansible 2.4 or higher
- Python PIP package manager
- The following PIP packages:
  - awscli
  - boto/boto3

You must also configure your local environment with your AWS credentials and you will also need to export AWS_DEFAULT_PROFILE, AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY to your shell env.

Role Variables
--------------

Following defaults are part of the role. You can change it as per your needs

- instance_type: t2.micro
- instance_region: ap-south-1
- ami_id: ami-e60e5a89

Dependencies
------------

None

Example Playbook
----------------

To use this role, you just need to run the site.yml or export the role in another playbook by simply checking out the directory & pointing the role name as `aws_ec2` as shown in site.yml file

License
-------

BSD

Author Information
------------------

by [Shankar Ramanathan](https://linkedin.com/in/shankar-ramanathan-a5715b9/)