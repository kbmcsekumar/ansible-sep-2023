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
  - Docker SWARM
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
- develped by Michael Deehan in Python language
- helps in automating software installations/configuration typically automating any administrivative activities on a existing OS/Virtual machine
- comes in 3 flavours
  1. Ansible Core - opensource, supports command-line interface only, can be installed only in Linux/Mac
  2. AWX - opensource, supports Web Interface, playbook can be executed but not create, developed on top of Ansible Core
  3. Red Hat Ansible Tower - developed on top of AWX, hence supports Web Interface
- Domain Specific Language(DSL)
  - the langauge in which the automation code is written
  - DSL used by Ansible is YAML (Yet Another Markup Language)
## Ansible High Level Architecture
![Ansible High-Level Architecture](AnsibleHighLevelArchitecture.png)

## Ansible Alternate Tools
- Puppet
- Chef
- Salt/SaltStack

## Installing Ansible
<pre>
https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html
</pre>

# Ansible Commands

## Lab - Cloning TekTutor Training Repository
```
cd ~
git clone https://github.com/tektutor/ansible-sep-2023.git
cd ansible-sep-2023
```

## Lab - Finding Ansible version
```
ansible --version
```

Expected output
<pre>
┌──(jegan㉿tektutor.org)-[~/ansible-sep-2023/Day2]
└─$ ansible --version
ansible [core 2.14.9]
  config file = Nonecustom
  configured module search path = ['/home/jegan/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/jegan/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible
  python version = 3.11.2 (main, Mar 13 2023, 12:18:29) [GCC 12.2.0] (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True
</pre>

## Lab - Building Custom Docker Image

We need to create key pair as shown below with default options
```
ssh-keygen
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/227827a8-87a4-435e-943e-6519ff2759ee)

## Lab - Building custom ubuntu ansible docker image
```
cd ~/ansible-sep-2023
git pull
cd Day2/CustomDockerImages/ubuntu
cp ~/.ssh/id_rsa.pub authorized_keys

docker build -t tektutor/ansible-ubuntu-node:latest .
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/cd4c5a3f-a54b-42ef-90e5-ec211c94a466)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/49ce0204-1227-4ee4-b4b6-3cce9d337b7d)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/f598d61b-5639-4bee-aaad-90131dd62181)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/03d8f633-017e-4230-9df5-1b25e95505e1)
![Port Forwarding](portforwarding.png)

## Lab - Creating ubuntu1 and ubuntu2 container using our Custom Ubuntu Ansible node image
```
docker run -d --name ubuntu1 --hostname ubuntu1 -p 2001:22 -p 8001:80 tektutor/ansible-ubuntu-node:latest
docker run -d --name ubuntu2 --hostname ubuntu1 -p 2002:22 -p 8002:80 tektutor/ansible-ubuntu-node:latest 
docker images
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/9fd1c67e-c9c6-4b0e-8260-ae8f2fbdf664)

# Lab - Testing if we are able to ssh into ubuntu1 and ubuntu2 container
```
ssh -p 2001 root@localhost
exit
ssh -p 2002 root@localhost
exit
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/e81e78bc-7cc3-436e-b730-ded353e08c43)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/bbed3807-8b88-44ee-bdd6-7b14c1b76608)

## Lab - Running ansible ad-hoc command to ping the ansible nodes
```
cd ~/ansible-sep-2023
git pull
cd Day2/static-inventory
ansible -i inventory all -m ping
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/795ca02e-9ffb-4b29-87e2-271edeb8ab12)

## Lab - Ansible ping with verbosity enabled upto 4 levels for troubleshooting/debugging purpose
```
cd ~/ansible-sep-2023
git pull
cd Day2/static-inventory
ansible -i inventory all -m ping -vvvv
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/301b11b3-a3cf-4864-9549-a4575770d22f)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/8c2f37b5-2911-497f-81e7-3f10f25434bc)

## Lab - Using Ansible configuration file to point out the inventory ansible must be using
```
cd ~/ansible-sep-2023
git pull
cd Day2/static-inventory
cat ansible.cfg
ansible all -m ping
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/6a4bab1f-164c-43e8-b991-ad177a4b1d6c)

## Lab - Using ansible setup module to collect facts about ubuntu1 ansible node
```
cd ~/ansible-sep-2023
git pull
cd Day2/static-inventory
ansible all -m setup
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/59505ca0-a28c-4bd0-a5da-76316cf185eb)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/dbe95464-3d5e-4f14-92dd-3a01a6547a58)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/f75fcec4-4eb7-4f8b-890e-85afacdd6662)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/5fdb77a1-328b-413d-abdc-9e4e902b3292)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/e989c468-4c8a-46ce-a86b-dd0deffc1f2d)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/9164dfb9-369c-4a49-a3eb-e74fa0486da8)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/5d4f316b-5694-436d-a061-5ef98cb167bd)

## Lab - Getting help about ansible modules
```
ansible-doc -l
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/f563c433-d120-4543-aacc-5b1ae0fdc43c)

## Lab - Finding total number of ansible modules supported by your version of Ansible
```
ansible-doc -l | wc -l
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/f11d3aa6-0e9d-4a47-881c-6e35132cbd59)

## Lab - Getting help info about any ansible module
```
ansible-doc ping
ansible-doc shell
ansible-doc copy
ansible-doc file
ansible-doc template
ansible-doc service
ansible_doc docker_image
ansible_doc docker_container
ansible_doc setup
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/4953451b-35a1-4463-87b5-6e9d2540c02b)

## Ansible Playbook Structure
![Ansible Playbook Structure](ansible-playbook-structure.png)


## Lab - Running your first ansible playbook
```
cd ~/ansible-sep-2023
git pull
cd Day2/playbooks
ansible-playbook -i ../static-inventory/inventory ping-ansiblenode-playbook.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/3bab3460-c6fb-41bd-9c0e-fb65bfd25852)

## Lab - Performing syntax checking without running the playbook
```
cd ~/ansible-sep-2023
git pull
cd Day2/playbooks
ansible-playbook -i ../static-inventory/inventory ping-ansiblenode-playbook.yml --syntax-check
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/9bd96cf4-7433-4310-9b77-6f231dfa0498)


## Lab - Refactoring the inventory file, moving all common variable as group variables
```
cd ~/ansible-sep-2023
git pull
cd Day2/playbooks
cat ansible.cfg
cat hosts
ansible all -m ping
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/49b5a156-553a-4c85-86e7-1df3baf9959b)

Capturing the output of ansible ad-hoc command
```
ansible ubuntu1 -m ping -vvvv > out.yml 2>&1
```

## Lab - Running the install nginx playbook
```
cd ~/ansible-sep-2023
git pull
cd Day2/playbooks
cat ansible.cfg
cat hosts
ansible-playbook install-nginx-playbook.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/dbe68949-52ab-48bf-98e9-edacb518f80b)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/88d9134d-1fe3-4e12-9cb1-225c71a66116)

Let's us check if the html page is accessible from ubuntu1 and ubuntu2 ansible nodes
```
curl http://localhost:8001
curl http://localhost:8002
ansible ubuntu1 -m shell -a "service nginx status"
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/c747211b-36b3-451b-9b74-3215e245d4b2)


Let's run the refactored playbook
```
cd ~/ansible-sep-2023
git pull
cd Day2/playbooks
cat ansible.cfg
cat hosts
ansible-playbook install-nginx-playbook.yml

curl http://localhost:8001
curl http://localhost:8002
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/821ff650-9b4c-4a92-bdd1-e4b206f353b8)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/597c1387-6abf-4785-9107-0efa50dd78d0)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/651e6148-8ee3-48f9-ba33-7d6e1c72738c)

Running the refactored playbook
```
cd ~/ansible-sep-2023
git pull
cd Day2/playbooks
cat ansible.cfg
cat hosts
ansible-playbook install-nginx-playbook.yml

curl http://localhost:8001
curl http://localhost:8002
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/53ba3cb9-27b5-4a2f-afb1-3f8f71a7f1f0)

