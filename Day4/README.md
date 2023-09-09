## Reference 
Other types of ansible loops
https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_loops.html

## Lab - Using list variables in Ansible playbooks
```
cd ~/ansible-sep-2023
git pull
cd Day4/loops
ansible-playbook using-list-in-playbook.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/1db1437c-7d05-4945-bcdc-4138f7cd4aa1)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/fec69a2c-0e8f-4c67-b091-0beb0581f785)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/16d7cadf-5868-47dc-a089-9b716a652d7c)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/c7989d2d-6f46-483b-9675-3c67e552d02f)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/6ef83cca-41eb-4172-b631-e8ee7ecd2ace)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/562b85e7-f655-4f2b-85a3-bde102bf156a)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/74ca4e90-0fb2-410f-a5d8-4a8105812867)

## Lab - Using dictionary variable in Ansible playbooks
```
cd ~/ansible-sep-2023
git pull
cd Day4/loops
ansible-playbook using-dictionary-in-playbook.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/be380369-aa1e-4d11-a715-922d359cb026)

## Lab - Cloning GitHub repo from ansible playbooks
```
cd ~/ansible-sep-2023
git pull
cd Day4/git-modules
ansible-playbook cloning-github-repo-using-playbook.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/092617b4-f406-4c10-bfc6-2246eec74584)

## Lab - Printing global git config 
```
cd ~/ansible-sep-2023
git pull
cd Day4/git-modules
ansible-playbook print-gitconfig-playbook.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/20503239-9815-461d-8774-07663111a1f0)

## Lab - Using Ansible recommended folder structure
```
cd ~/ansible-sep-2023
git pull
cd Day4/ansible-recommended-dir-structure
tree
cat host_vars/centos1
cat host_vars/centos2
cat host_vars/ubuntu1
cat host_vars/ubuntu2
cat group_vars/all

ansible all -m ping
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/bb95a532-70d5-465a-8862-5f0c65d874b8)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/82ca9f9c-a69d-4297-ac1a-d5e66bdc71fa)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/51154927-b605-4dc3-9aad-774a333b345e)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/94d6abea-b2d1-4b9c-a0a3-14cb11dbf68c)


## Ansible vault overview
- used to securely save server login credentials in an encypted fashion
- playbook can securely retrieve the vault protected values and use them
- ansible-vault allows to create new vault file which is pass-protected
- ansible-vault allows us to edit existing vault file which is pass-protected
- ansible-vault allows us to view existing vault file which is pass-protected
- ansible-vault allows to encrypt any existing text file with a password
- ansible-vault allows to decrypt any existing vault protected file

The following options are supported by ansible-vault
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/098888ff-4aa7-4748-bbe6-14a00988a32e)

## Lab - Creating a new vault protected file
I have used root as my vault password.
```
cd ~/ansible-sep-2023
git pull
cd Day4/vault
ansible-vault create mysql-login-credentials.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/19b11861-780f-4f97-9074-c30ce937c67c)

## Lab - Editing ansible-vault protected file
You need to type root as the password while editing in case you are using the file that I created, otherwise you will have to type the password you gave at the time of creating the vault file.
```
cd ~/ansible-sep-2023
git pull
cd Day4/vault
ansible-vault edit mysql-login-credentials.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/8a5bd632-16be-4f01-a21b-54c03f984b87)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/49f03fc5-38bc-467d-9f14-e3739432c7e3)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/d5d2ee11-1ecc-4964-bbd0-11444620a430)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/82ed2b39-e294-441a-be8f-ad553644d2db)


## Lab - Displaying ansible-vault protected file values
You need to type root as the password while editing in case you are using the file that I created, otherwise you will have to type the password you gave at the time of creating the vault file.
```
cd ~/ansible-sep-2023
git pull
cd Day4/vault
ansible-vault view mysql-login-credentials.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/e632a610-61e9-4ce4-b6ba-08e78fbdf689)


## Lab - Encrypting plain text file or Decrypting existing vault protected file
```
cd ~/ansible-sep-2023
git pull
cd Day4/vault
cat mysql-login-credentials.yml
ansible-vault decrypt mysql-login-credentials.yml
cat mysql-login-credentials.yml
ansible-vault encrypt mysql-login-credentials.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/6748a48a-c345-4f75-af60-f690ee7952f3)


## Lab - Changing the password of an ansible vault protected file using rekey

First type your existing password, followed by the new password and confirm the new password.
```
cd ~/ansible-sep-2023
git pull
cd Day4/vault
ansible-vault rekey mysql-login-credentials.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/1508dfd6-d560-484a-9c6b-763a1dcd7a70)

## Lab - Accessing values stored within vault protected files safely from playbook
```
cd ~/ansible-sep-2023
git pull
cd Day4/vault
ansible-playbook reading-values-from-vault-protected-file-playbook.yml  --ask-vault-pass
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/bf4c319a-8b9c-43dd-b1e6-f3f5f561aee0)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/1ffea681-3c71-41d8-b3bb-655bc9cec0dd)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/249d7db6-74c0-4ea3-bcfc-ca68e820867c)


## Lab - Retrieving values from vault protected files picking the vault password from a hidden file 
```
cd ~/ansible-sep-2023
git pull
cd Day4/vault
cat mysql-login-credential.yml
cat oracle-login-credential.yml
cat ansible.cfg
cat .password
ansible-vault view oracle-login-credential.yml
ansible-vault view mysql-login-credential.yml
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/5c6f7370-9665-464d-8f9f-9c7f11bde7a3)



## Lab - Pinging a Windows ansible node

Let's see what happens if we attempt to ping a windows ansible node ( try this in Ubuntu machine )
```
cd ~/ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible -i inventory all -m ping
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/c80d079b-8ac5-4ace-b88c-7f06dc986e0e)

### We need to configure WinRM connectivity in the Windows Ansible Node

#### Windows Node Ansible Requirments	
- PowerShell 3.0 or latest
- .Net Framework 4.5 or latest

### Finding PowerShell version from Windows Powershell prompt
```
$PSVersionTable
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/a9722c67-f55f-482c-a4f1-1fa4beb95b1b)


### Finding .Net Framework Version

1. Open regedit

2. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/8d97cfef-0cc0-4d81-a303-1d7d1d6ca7ac)


### Configuring WinRM on Windows machine
Download the file at below URL and save it in C:/Users/Administrator/Downloads/ConfigureRemotingForAnsible.ps1
```
https://github.com/ansible/ansible-documentation/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1
```

Now execute the below command
```
powershell.exe -ExecutionPolicy ByPass -File C:/Users/Administrator/Downloads/ConfigureRemotingForAnsible.ps1

winrm enumerate winrm/config/Listener
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/08821a8e-2b7b-47d7-8ab9-6b8581781ae1)


### Configuring Windows node with Basic authentication
```
Set-Item -Path WSMan:\localhost\Service\Auth\Basic -Value $true
```

### Verify if WinRM Listeners are running ( 2 listerners one for Http and other for Https expected )
```
winrm enumerate winrm/config/Listener
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/23e5d406-e105-4c12-8786-215df8af72a1)


### On the Ansible Controller machine (Ubuntu machine), make sure pywinrm is installed
```
pip install "pywinrm>=0.3.0"
```

## Lab - Pinging a windows ansible node from a Linux Ansible Controller Machine (try this in Ubuntu)
```
cd ~/ansible-feb-2023
git pull

cd Day4/windows-ansible-node/
ansible -i inventory -m win_ping
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/14e211ce-2403-4e72-80ca-25ff2c2908ff)

# Lab - Installing choco.exe to enable playbook using win_chocolatey ansible module

In your windows lab machine, using chrome browser download the below powershell, save this file in C:/Users/Administrator/Downloads folder.
```
https://community.chocolatey.org/install.ps1 
```

From windows command prompt, issue the below command
```
powershell.exe -ExecutionPolicy ByPass -File C:/Users/Administrator/Downloads/community.chocolatey.org_install.ps1
```

In case you got error, you will have to reboot the windows and try this again.

Once it is installed successfully, you can try running the ansible-playbook as usual from Ubuntu lab machine.

## Chocolatey portal URL
<pre>
https://community.chocolatey.org/packages  
</pre>

## Lab - Copying file from Ansible Controller Machine to Windows Ansible Node using Ansible Playbook
```
cd ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible-playbook copy-file-playbook.yml
```

## Lab - Creating windows registry entry from ansible playbook
```
cd ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible-playbook create-registry-entry-playbook.yml
```

## Lab - Installing JDK, Maven, build application, create windows service and start service for custom build spring-boot appplication
```
cd ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible-playbook create-service-playbook.yml
```

## Lab - Install git for windows using ansible playbook
```
cd ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible-playbook install-git-for-windows-playbook.yml
```

## Lab - Install httpd web server in windows using ansible playbook
```
cd ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible-playbook install-httpd-in-windows-playbook.yml
```

## Lab - Rebooting windows machine
```
cd ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible-playbook reboot-windows-machine-playbook.yml
```

## Lab - Rebooting windows machine asynchronously without blocking
```
cd ansible-sep-2023
git pull
cd Day4/windows-ansible-node
ansible-playbook reboot-windows-machine-async-poll-playbook.yml
```

## Lab - Error handling in ansible playbooks
```
cd ansible-sep-2023
git pull
cd Day4/windows-playbook-errorhandling
ansible-playbook playbook.yml
```

## Lab - Loops and Jinja Templating in ansible playbooks
```
cd ansible-sep-2023
git pull
cd Day4/loops-and-jinja
ansible-playbook playbook.yml
```

## Lab - Using regular expressions in ansible playbooks
```
cd ansible-sep-2023
git pull
cd Day4/regular-expressions
ansible-playbook playbook.yml
```
