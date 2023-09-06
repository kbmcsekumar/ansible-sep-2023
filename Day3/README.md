## Using Template module to customize files before it is copied onto the ansible nodes
```
cd ~/ansible-sep-2023
git pull
cd Day3/playbooks
ansible-playbook install-nginx-playbook.yml
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/1348fd18-dca0-45f9-9edc-21076c2d9cf3)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/908b4c6e-32fc-4a56-a4da-ccb35da14624)

## Lab - Building Custom Ubuntu Ansible Node Docker Image
```
cd ~/ansible-sep-2023
git pull
cd Day3/CustomDockerImages/centos
cp ~/.ssh/id_rsa.pub authorized_keys
docker build -t tektutor/ansible-centos-node:latest .
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/5798b6d4-8a74-4727-bc5f-7b0d581f911b)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/aa1a2846-7f61-4508-ac60-4bb9e628eafe)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/364387fc-3ad4-4fe9-8f58-e473aeca24c4)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/95acb054-0aaf-4909-94fd-c8bbd6442d5f)
