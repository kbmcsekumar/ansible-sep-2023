# Configuring a Windows Ansible node
## Configuring Windows Ansible Node

Windows Node Ansible Requirments	
- PowerShell 3.0 or latest
- .Net Framework 4.5 or latest

### Finding PowerShell version

$PSVersionTable

### Finding .Net Framework Version

1. Open regedit

2. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full

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
