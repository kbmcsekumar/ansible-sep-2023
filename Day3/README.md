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
docker images
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/5798b6d4-8a74-4727-bc5f-7b0d581f911b)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/aa1a2846-7f61-4508-ac60-4bb9e628eafe)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/364387fc-3ad4-4fe9-8f58-e473aeca24c4)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/95acb054-0aaf-4909-94fd-c8bbd6442d5f)
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/27a0d0b8-0943-4460-beaf-b243774e321b)

## Lab - Creating centos1 and centos2 containers using the newly build custom centos docker image
```
docker images
docker run -d --name centos1 --hostname centos1 -p 2003:22 -p 8003:80 tektutor/ansible-centos-node:latest
docker run -d --name centos2 --hostname centos2 -p 2004:22 -p 8004:80 tektutor/ansible-centos-node:latest
docker ps
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/19b9a5c6-c594-447f-be03-579f5b02c938)

## Lab - Testing if we are able to SSH into the centos1 and centos2 containers
```
docker ps
ssh -p 2003 root@localhost
exit
ssh -p 2004 root@localhost
exit
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/e356e05b-de00-44ef-9a1a-73694760d771)
