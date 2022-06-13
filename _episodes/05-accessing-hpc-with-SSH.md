---
title: "05 Accessing HPC with SSH"
teaching: 20
exercises: 15
questions:
- "How to connect to Sumhpc"
objectives:
- "Understand how ssh and related tools are used to connect to HPC resources"
keypoints:
- "ssh is the preferred way to connect to linux servers"
- "ssh is cryptographically secure and protects information sent"
- "ssh is supported on sumhpc"
- "sftp available in a command line application and in GUI based applications including cyberduck, winSCP, mobaXterm, and many Unix/Linux file system managers ( ___ Mac, __ ubuntu, and __ Debian, ___ Linux Mint ). "
- "rsync and globus are other file transfer applications in common use."

---
FIXME

{% include links.md %}

# SSH Basics

The take home from this lesson.

- Use the command `ssh <username>@<remote server IP address|domain name>` to connect to a remote server.

- other tools exist for connecting and transfering files to the remote server using the ssh protocol including sftp and rsync.

The details on how ssh works

- The client asks the remote server (sumhpc login node) to establish a connection
- The remote server then sends a public key to the client (this is done automatically with the ssh command you do not need to generate a key for this). 
- The client stores the public key in its known host file (this is done automatically with the ssh command you do not need to generate a key for this). 
- (Gotcha) if the remote server changes its public ssh key you may need to clean remove the previous ssh key from your list of known hosts. You can contact your system adminstrator if this happens, before making any changes. 


INSERT FIGURE OF SSH


Figure 06.01 shows the basics on how ssh establishes a secure 


Using ssh to connect to remote server. 


- Open terminal 

- type `ssh <username>@<remote server IP address|domain name>` where use name is you user name on the **remote** system 


Example ssh connection for this class

- open terminal 

- type `ssh user@<remote server IP address>` where use name is you user name on the **remote** system, instructor will provide remote IP address 

# SFTP 

SFTP stands for secure file transfer protocol and is used to transfer files from one computer to another. Some commony used sftp client applications include CyberDuck, FileZilla, MobaXterm, and WinSCP. You can contact your desktop or laptop system admistartor for information regarding the installation of an sftp client. 


To connect to remote session with MobaXterm

## SFTP client usage 

MobaXtem will automatically establish and sftp session when ssh'ing into a remote system. It is possible to stand up an individual sftp session as well as seen below. 
