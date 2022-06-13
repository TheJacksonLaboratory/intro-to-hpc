---
title: "02 From Computer to HPC"
teaching: 10
exercises: 0
questions:
- "What are the components of a computer"
- "What is the difference between a regular computer and an HPC"
objectives:
- "Overview of General Computing"
keypoints:
- "HPCs are typically many large servers networked together"
- "HPCs utilized networked disk space instead of local disk space"
---


{% include links.md %}

# Computer Component Review

## CPU

CPUs are the data process unit, they are composed of multiple cores. For legacy reasons software often refers the number of cores as the number of CPUs, so yeah that is confusing. 
 
## RAM (a.k.a MEMORY)

RAM is fast digital storage. Most programs utilize RAM for access to data needed more than once. RAM is generally non-persistent when the powered off RAM memory is lost.

## DISK

Disk is persistent digital storage that is not as fast as RAM. Disk storage can be made up of on or more disks such as hard drives (HDD) and/or Solid State Harddrives (SSD). Multiple disk can be configured together for increased performance and drive failure protection. 

## NETWORKING

Networking 

## GPU

A Graphics Processing Unit (GPU) 

# Consumer Computer vs Servers vs HPC vs Sumhpc

| Component | Home/Busines Computer | Server     | Typical Individual  Node in HPC | Typical Total HPC System | Individual  Node on Sumhpc | Total Sumhpc System | 
|-----------|-----------------------|------------|-------------------------------|--------------------------|---------------------------|---------------------|
| CPU (cores)| 4 - 8 | 12 - 128  | 32 - 128 | 1000s | 70\* | 7,000 |
| RAM(GB) | 8 -17 | 64 - 960 | 240 - 3000 | 64,000 | 768 - 3TB | 76.8 TB|
| DISK (TB)| .5 - 1 TB | 8 - 100 | None - 1 TB | 100s (Networked) | ? | ???? |
| Networking (Gbe)| .1 - 1 | 1 - 10 | 40 - 100 | 40 - 100 | 40 | 40 - ???? |

\* note Sumhpc High Mem nodes contain 142 cores each and 3TB of RAM.


# HPCs are servers networked together and managed with a scheduler

