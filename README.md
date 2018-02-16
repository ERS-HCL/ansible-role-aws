ansible-role-aws
================

An Ansible role that creates EC2 instances, Security groups in AWS cloud environment. 
Public DNS names of the EC2 instances are updated in the inventory file for further use in other roles/playbook.

This role has the support for delete,stop and start the EC2 instances apart from create.

Requirements
------------

python package version 2.6 or greater is installed on the ansible machine.
boto  package installed on the ansible machine.
AWS access key environment variables AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY need to be set.
AWS key pair should be created to connect to the instances.

Role Variables
--------------

Available Variables are listed below, they can be defined for all the 
instances in the default/main.yml or individually in the inventory file.

   AWS region where the EC2 instance has to be created

     aws_region: ap-south-1

   AWS instance type to specify the CPU and memory requirement

     instance_type: t2.micro

   AWS image ID to identify the OS and host the machine

     image_id: ami-ac1e68c3

   AWS security group the instances will be attached to.
   if it is not available already, new group will be created with limited access

     security_group_name: "security123"

   AWS Key pair to connect to the AWS instance, create it manually.

     sshkeypair_name: my_key

   AWS EBS storage disk size to be provisioned in GB

      disk: 10


Dependencies
------------

none 

Example Playbook
----------------

Creating EC2 instances in AWS cloud.

	- hosts: instances
	  connection: local
	  vars:
	    operation: createhosts

	  roles:
	    - SathiyarajPeriyannan.aws

Starting EC2 instances in AWS cloud.

	- hosts: instances
	  connection: local
	  vars:
	    operation: starthosts

	  roles:
	    - SathiyarajPeriyannan.aws

Stoping  EC2 instances in AWS cloud.

	- hosts: instances
	  connection: local
	  vars:
	    operation: stophosts

	  roles:
	    - SathiyarajPeriyannan.aws

Deleting  EC2 instances in AWS cloud.

	- hosts: instances
	  connection: local
	  vars:
	    operation: deletehosts

	  roles:
	    - SathiyarajPeriyannan.aws

License
-------

BSD

Author Information
------------------

This role was created in 2018 by Sathiyaraj Periyannan 
