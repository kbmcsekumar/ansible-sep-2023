## What is Provisioning Tool?
- helps in creating a new Virtual Machine in the onPrem infrastructure, public/private/hybrid cloud
- automating OS installation
- Examples
  - Docker, Vagrant, Cloudformation, Terraform
- Terraform also supports some minimal Configuration Management Features

## What is Container Orchestration Platform?
- helps in managing your containerized application workloads
- helps in setting up High Available application within Container Orchestration Platform
- provides inbuilt monitoring tools
- supports scale up/down depending on the user traffice to your application workloads
- helps in exposing your application to external world using external Services
- helps in restriction your application access to only within the cluster using internal service
- self-healing platform
- Examples
  - Docker SWAR
  - Google Kubernetes
  - Red Hat OpenShift

## What is Configuration Management Tool?
- helps in automating software installation and configuration on a existing OS/Virtual machine in OnPrem servers, public/private/hybrid cloud environments
- also helps create users with specific access
- Ansible also supports some minimal provisioning features
 
## Provisioner vs Configuration Management Tool
- The strength of Provisioner tools is in creating a new Virtual Machine in OnPrem/Cloud environments
- Provisioner also supports some basic configuration management features, but it doesn't or can't replace the Configuration Management tools
- Generally provisioning tools like Terraform creates the Virtual Machine and then invoke Ansible to further configure the machine

## Ansible Overview
- is a Configuration Management tool
- helps in automating software installations/configuration typically automating any administrivative activities on a existing OS/Virtual machine
- comes in 3 flavours
  1. Ansible Core - opensource, supports command-line interface only, can be installed only in Linux/Mac
  2. AWX - opensource, supports Web Interface, playbook can be executed but not create, developed on top of Ansible Core
  3. Red Hat Ansible Tower - developed on top of AWX, hence supports Web Interface

## Ansible High Level Architecture
![Ansible High-Level Architecture](AnsibleHighLevelArchitecture.png)

## Ansible Alternate Tools
- Puppet
- Chef
- Salt/SaltStack
