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

## Lab - Pinging a Windows ansible node

Let's see what happens if we attempt to ping a windows ansible node
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


### On the Ansible Controller machine, make sure pywinrm is installed
```
pip install "pywinrm>=0.3.0"
```

## Lab - Pinging a windows ansible node from a Linux Ansible Controller Machine
```
cd ~/ansible-feb-2023
git pull

cd Day4/windows-ansible-node/
ansible -i inventory -m win_ping
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/14e211ce-2403-4e72-80ca-25ff2c2908ff)
