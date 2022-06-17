---
title: "08 Sumhpc"
teaching: 10
exercises: 0
questions:
- "What is Sumhpc"
objectives:
- "Review of Sumhpc notes"
keypoints:
- "Sumhpc has 3 compute node types compute, high_mem, and dev."
- "The compute node types refer to partitions in the slurm configuration."
---

{% include links.md %}

## Sumhpc Basics

- Sets of nodes are called partitions within slurm. 

- We have 3 sets of nodes (a.k.a. partitions) each with distict properties:

 - **compute** : General compute nodes 70 core and 760GB each.

 - **high_mem**: For jobs with large RAM requirements (job requiring more than 760GB of RAM), these nodes have 142 processors each and almost 3TB of RAM each.  

 - **dev** : Dev nodes have faster processors but less memory than compute and high_mem nodes,  these nodes have 30 processors each and 180GB of RAM each.  


|                        | compute    | high_mem   | dev             |
|:-----------------------|:----------:|:----------:|:---------------:|
| # of nodes             | 100        | 2          | 20              |
| Usable memory per node | 760GB      | 3022GB*    | 180GB           |
| Usable cores per node  | 70         | 142        | 30              |
| CPU core speed​​​​​​​         | 2.70GHz    | 2.70GHz    | 3.60GHz         |
| Total partition MEM    | 76T        | 6T         | 3.6T            |
| Total partition cores  | 7000       | 284        | 600             |
| how to use?            | -p compute | -p high_mem| -p dev & -q dev |

\*Note:   The max available memory on the high_mem nodes is 3022GB, just shy of 3TB (3072GB binary unit), also the '--mem' value is required to be an integer (no decimals). 

\**Note:   To use the dev partition you must use both the -p dev and -q dev when submitting jobs.  See QOS.