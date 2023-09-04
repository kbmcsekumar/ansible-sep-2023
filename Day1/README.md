# Kindly complete the pre-test from your RPS Lab machine
- Once you login to your RPS Lab machine, you will see a web browser with the below URL kept open
- Copy/Paste from your work/personal machine to/from RPS Lab machine is disabled as per your company policy
- Kindly provide your full name and personal email id while registering for the pre-test
- Once you complete the pre-test, kindly confirm me either orally or leave a message via WebEx chat if you have access
  to WebEx chat
- Once everyone completes the pre-test we can start the training until then I'll be on mute
- For any lab acces issues, please write to the RPS Tech Team user logged in via WebEx chat, you may have to share the RPS cloud user name and describe the technical challenge to    
<pre>
https://app.mymapit.in/code4/tiny/VxOr50  
</pre>

## Installing network tools in Ubuntu lab machine
```
sudo apt install -y net-tools iputils-ping
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/2d9ba90e-b01d-4598-ad77-d0823e03aebe)


# Docker Overview

## What are Bootloaders?
- are system utilities that helps in setting up dual/multi boot in your laptop/desktop/workstation
- i.e you can install 3~4 Operating System on your laptop/desktop/workstation
- but only one OS can be active at any point of time
- If you switch on your laptop with once the BIOS POST(Power On Self Test) completes, the BIOS
  will instruct the CPU to execute the system utility at Sector 0, Byte 0 in your Hard Disk. The Sector 0, Byte 0 is 512 bytes and it is referred as Mater Boot Record (MBR)
- the Boot Loader System utility is installed on the MBR of your Hard disk
- Boot Loader will scan your Hard disk searching for Operating Systems, if it detects more than one Operating System, then it gives a menu for you to choose to select which OS you wish to boot into
- Let's say you booted machine into Windows, but you need Ubuntu, you first have to shutdown Windows and boot into Ubuntu and vice versa
- Only one OS can be active at any point of time
- Examples
  - LILO (Linux Loader - opensource)
  - GRUB1 - opensource
  - GRUB2 - opensource
  - For Mac users, BootCamp you can boot into windows on a Mac OS-X
  
## What is Hypervisor?
- many OS can be running side-by-side on the same laptop/desktop/workstation/servers
- i.e many OS can be active at the same time
- Virtualization technology
- this is a combination of Hardware + Software technology
- Processors
  - AMD
    - AMD-V - Virtualization Feature set supported in the Processor
  - Intel
    - VT-X - Virtualization Feature set supported in the Processor
- there are two types of Hypervisors
  1. Type1 - used in Servers ( Bare-metal Hypervisors - can be installed directly on a HW )
  2. Type2 - used in Laptops/Desktops/Workstations ( requires Host OS - Unix/Linux/Windows/Mac)
- Examples
  VMWare 
   - Workstation - Linux & Windows(type2)
   - Fusion - Mac OS-X (type2)
   - vSphere/vCenter - Bare-metal Hypervisor (type 1)
  Oracle virtualbox (type2 - Free)
  Parallels (type2 - Mac OS-X)
  Microsoft Hyper-V

## In the absence of Virtualization technology, how many minimal physical servers are required to support 1000 active OS?
1000 Physical servers are required

## With Virtualization technology, how many minimal physical servers are required to support 1000 OS?
250 Physical Servers - each supporting 4 Virtual Machines

Processors with multiple CPU Cores
- AMD Processors it comes with 128 CPU Cores

Processors comes in 2 form factors
- SCM ( Single Chip Module ) - One IC will host one Processor
- MCM ( Multi Chip Module ) - Once IC will host multiple Processors

Server Motherboards with 4 Sockets

Let's say MCM Processor with 4 Processor per IC
Each Processor supporting 128 CPU Cores
1 Socket = 4 Processors with 128 CPU Cores on each Processor = 4 x 128 x 4 = 2048

Hyperthreading - each Physical CPU Core is capable of running 2 threads parallely 
Hence, Hypervisor softwares will see each Physical CPU Cores as 2 Virtual Cores

2048 x 2 = 4096 virtual cores

MacBook Pro with Quad Core Processor, 16 GB RAM and 1 TB HDD
- I used to 2 VMS + 1 Host OS(Mac)


## Enable the Docker Server REST API or TCP Socket
Check the status of docker service to find the path of docker service configuration file
```
sudo systemctl status docker
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/507c9c31-20b0-4522-9c91-3d3720cdeb1d)


You can edit the /lib/systemd/system/docker.service file as Administrator and append tcp://0.0.0.0:4243 at line 13 as shown below
```
sudo vim /lib/systemd/system/docker.service
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/545d9fbc-db55-418e-ab18-dc74578cf819)

You need to restart docker service to apply the config changes
```
sudo systemctl daemon-reload
sudo systemctl restart docker
sudo systemctl status docker
```
Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/98e82f0e-51fa-4627-9860-2dbe3fb5c9d8)

  
## What is Docker?

## Hypervisor vs Docker

## Hypervisor High-Level Architecture

## Docker High-Level Architecture

# Docker Commands

## Demo - Connecting your local Docker client to a remote Docker server
You need to do this on your local machine
```
export DOCKER_HOST=tcp://<ip-address-of-machine-where-docker-server-is-running>:4243
docker images
```

## Lab - Finding docker version
```
docker --version
```
Expected output
<pre>
┌──(jegan㉿tektutor.org)-[~/ansible-sep-2023]
└─$ docker --version
Docker version 20.10.25+dfsg1, build b82b9f3  
</pre>

## Lab - Listing docker images from Local Docker Registry
```
docker images
```

Expected output
<pre>
┌──(jegan㉿tektutor.org)-[~/ansible-sep-2023]
└─$ docker images
REPOSITORY                     TAG        IMAGE ID       CREATED         SIZE
tektutor/ansible-centos-node   latest     67e2c2ee6256   2 days ago      428MB
tektutor/ansible-ubuntu-node   latest     a3f39aea7460   2 days ago      220MB
centos                         7.9.2009   eeb6ee3f44bd   23 months ago   204MB
ubuntu                         16.04      b6f507652425   2 years ago     135MB  
</pre>

## Lab - Docker Remote Registry
Open the below URL on your Ubuntu Cloud machine chrome web browser, click on Exlore
```
https://hub.docker.com
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/b1f1c9b8-c1ed-4ae4-97f0-8bf2229ae44c)

## Lab - Downloading the hello-world docker image from Docker Hub Remote Registry to your local docker registry
```
docker pull hello-world:latest
```

Expected output
![image](https://github.com/tektutor/ansible-sep-2023/assets/12674043/f62c5e79-98bc-447d-8996-58e0f25d5c0b)
