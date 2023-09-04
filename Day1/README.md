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

  
## What is Docker?

## Hypervisor vs Docker

## Hypervisor High-Level Architecture

## Docker High-Level Architecture
