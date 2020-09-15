# devops-2
DevOps#2 project - Carlos Ijalba 2020.

Terraform setup for AWS to create 4 machines in a VPC:

       1.- web1, with nginx
       2.- web2, with apache2
       3.- prom1, with prometheus
       4.- graf1, with grafana

The VPC will create the following ojects:

      1x VPC
      1x DHCP option set
      1x internet gateway
      3x private subnets
      3x public subnets
      1x private route table
      1x public route table
      1x route table association, associate Private subnet with Private Route Table
      1x route table association, associate Public subnet with Public Route Table
      renames the default SG
      renames the default NACL
      1x SG for SSH
      1x IAM role

      all with at least 2 TAGS:
        -Name
        -Environment

This project will have the following premises:

  1.- All boxes will use Debian Linux. 

  2.- The instances will be built from a provided box (we will not make our own), only customize the existing ones to suit our needs (easier). In a sepparate project we will use packer to do our own customized images
  to deploy instances.

  3.- The software in each instance will be provisioned via Ansible playbooks. Ansible itself will be provisioned via bash scripts under a terraform shell provisioner.

  4.- prom1 will be the Ansible control node.

  5.- if some software is too complex to install/configure via ansible scripts (prometheus/grafana), then bash scripts will be fired from terraform under shell provisioners.

  6.- a static web site mut be deployed in nginx and in apache2 using the same code.

  7.- all the infra must be registered and monitored via prometheus/grafana.

  8.- the infrastructure must be inmutable, and recorded in git.

#
