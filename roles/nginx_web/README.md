Role Name
=========

Installing & setting up Nginx in Red-hat 7.4, setting up jinja2 template & terminating the EC2 instance created by role `aws_ec2`

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

The role references variable for red hat image `img_redhat` and default variable `target_dir` for dropping custom HTML file.

Dependencies
------------

Dependant on the role `aws_ec2` for creating the instance. This role can also be adopted for any environment by changing the hostvars of the role accordingly.

Incase you wish to adopt this role for another OS, you will need to change all the task yml files under `task` folder & the respective when task/clause needs to be modified for the OS of your choice

Example Playbook
----------------

To use this role, you just need to run the site.yml or export the role in another playbook by simply checking out the directory & pointing the role name as `nginx_web` as shown in site.yml file

License
-------

BSD

Author Information
------------------

by [Shankar Ramanathan](https://linkedin.com/in/shankar-ramanathan-a5715b9/)
