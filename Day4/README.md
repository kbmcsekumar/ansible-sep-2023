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
```
$url = "https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1"

$file = "$env:temp\ConfigureRemotingForAnsible.ps1"
```

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
```
powershell.exe -ExecutionPolicy ByPass -File $file
```

### Configuring Windows node with Basic authentication
```
Set-Item -Path WSMan:\localhost\Service\Auth\Basic -Value $true
```

### Verify if WinRM Listeners are running ( 2 listerners one for Http and other for Https expected )
```
winrm enumerate winrm/config/Listener
```

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
<pre>
jegan@tektutor.org $ <b>ansible -i inventory all -m win_ping</b>
192.168.180.130 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
</pre>
