---
title: "05 Accessing Remotes Systems with SSH"
teaching: 10
exercises: 0
questions:
- "How to connect to a remote system?"
objectives:
- "Understand how ssh and related tools are used to connect to HPC resources"
keypoints:
- "ssh is the preferred way to connect to linux servers"
- "ssh is secure and protects information sent"
- "sftp available in a command line application and in GUI based applications for file transfers"
---
{% include links.md %}

## SSH Basics

**The take home from this lesson.**

- Use the command `ssh <username>@<remote server IP address|domain name>` to connect to a remote server.

**The details on how ssh works.**

- The (local) client asks the remote server (sumhpc login node) to establish a connection.
- The server and the client work together to encrypt the contents of data transferred through the connection.

**Example ssh connection for this class**

- Open terminal 

- type `ssh <username>@<login node name>` where use name is your username on the remote system and the login node name (provided by instructor).

- Notice the first time you connect to a new machine you may get asked the following question (example listed below). 

```BASH
[user@edu-vm-63d1410f-2 ~]$ ssh user@35.227.70.171
The authenticity of host '35.227.70.171 (35.227.70.171)' can\'t be established.
ECDSA key fingerprint is SHA256:UTHv5IOvrF9uvxuh9Fo8uW2bx0BwCRLyrwHhONoiIj8.
ECDSA key fingerprint is MD5:15:bb:25:2a:3a:45:f4:c7:df:21:26:37:12:66:79:77.
Are you sure you want to continue connecting (yes/no)?
```
- Now your connected to the remote system, commands issued into the prompt are now being executed on the remote system.

- You are now on the login node notice the change in the prompt. 

- Do not run programs on the login nodes. We use the login node to access the compute nodes with ```srun``` and submit batch jobs with ```sbatch```. 

- Lets take a look around the directories. 

- Take a look at the home directory
```ls ~ ```

- Take a look at the fastsrcatch directory
```ls /fastscratch ```

- Take a look at the fastsrcatch directory
```ls /projects ```

- You can remain logged in for the rest of the tutorial, but when your ready to exit, just type ```exit`` on the terminal.  

## SFTP 

SFTP stands for secure file transfer protocol and is used to transfer files from one computer to another. 

MobaXtem will automatically establish and sftp session when ssh'ing into a remote system. It is visible as a yellow globe on the left hand side of the MobaXterm terminal. 

