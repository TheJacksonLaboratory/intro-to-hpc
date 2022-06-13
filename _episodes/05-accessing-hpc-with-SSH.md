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

- The (local) client asks the remote server (sumhpc login node) to establish a connection.
- The server and the client work together to encrypt the contents of data transfered through the connection.

Using ssh to connect to remote server. 


- Open terminal 

- type `ssh <username>@<remote server IP address|domain name>` where use name is you user name on the **remote** system 


Example ssh connection for this class

- open terminal 

- type `ssh user@<remote server IP address>` where use name is you user name on the **remote** system, instructor will provide remote IP address. Your username is user for this example 

- Notice the first time you connect to a new machine you may get asked the following question. 

```BASH
[user@edu-vm-63d1410f-2 ~]$ ssh user@35.227.70.171
The authenticity of host '35.227.70.171 (35.227.70.171)' can\'t be established.
ECDSA key fingerprint is SHA256:UTHv5IOvrF9uvxuh9Fo8uW2bx0BwCRLyrwHhONoiIj8.
ECDSA key fingerprint is MD5:15:bb:25:2a:3a:45:f4:c7:df:21:26:37:12:66:79:77.
Are you sure you want to continue connecting (yes/no)?
```
- If this is the system your looking to connect and you trust it type `yes`. 

- Now your connected to the remote system things that you enter in the terminal are now being exicuted on the remote system.

HERE CHALLANGE HERE TO SEE THE NEW SYSTEM.

- To disconnect type `exit`

# SFTP 

SFTP stands for secure file transfer protocol and is used to transfer files from one computer to another. Some commony used sftp client applications include CyberDuck, FileZilla, MobaXterm, and WinSCP. You can contact your desktop or laptop system admistartor for information regarding the installation of an sftp client. 

To connect to remote session with MobaXterm.

## SFTP client usage 

MobaXtem will automatically establish and sftp session when ssh'ing into a remote system. It is possible to stand up an individual sftp session as well as seen below. 
