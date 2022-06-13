---
title: "11 software on Sumhpc"
teaching: 10
exercises: 0
questions:
- How to connect to Sumhpc"
objectives:
- "Introduction to basic SLURM commands"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---
FIXME

{% include links.md %}

### Software Usage on the SumHPC Cluster

On Sumhpc, we have overhauled how researchers are able to install and easily access the software they need. Users are still able to download and install software into their userspace (`/projects` or `/home` directories). Additionally, low level development tools such as `gcc`, `openMPI`, `openJDK`, and basic libraires are still available via the `module` system. The new and exciting way we are able to provide software on Sumhpc, however, is through software containers. Singularity containers are a cutting edge way of creating your own custom software modules. Containers not only provide you with the software you need, but also a contained environment which ensure that your software runs the exact same way whether it's on your laptop, on the HPC resources, with a collaborator, or in the cloud. 

---
### Userspace Installation

The simplest method of installing software for use with Sumhpc is to install directly into your userspace. This includes any directories you have permissions to write to and modify. This includes your group's `/projects` directory or your personal `/home` directory. You also have write permissions on `/fastscratch` and `/tmp`, but these are not recommended due to their ephemeral nature. Most software installations will default to writing under a `/usr/` or `/lib/` path. Since these locations are shared by everyone, these "global" trees are not writable by the typical HPC user. Instead, many software installations will allow you to perform a "local" install in a directory of your choosing. Please consult the documentation for your software to find how to change the install path for your software. 

### Environment Modules

Now, only low-level software such as libraries, compilers, Singularity, and programming language binaries are available through modules. To see what modules are available, run the command `module avail`. For more information about how to use the `module` command, see the [documentation](https://modules.readthedocs.io/en/latest/). 

### Singularity Containers

The newest and most liberating change to software installations on HPC is the introduction of Singularity. Containerization allows you to install whatever software you want inside of a singular, stand-alone Singularity image file (`.sif`). This file contains your software, custom environment, and metadata all in one. 

To use Singularity, all you have to do is load the module by running `module load singularity` in a running job session on Sumhpc. Singularity can download new containers (`singularity pull`), run existing ones (`singularity run/exec/shell`), or upload new containers to registries (`singularity push`).

