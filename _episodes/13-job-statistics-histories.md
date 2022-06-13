---
title: "13 job statistic and history"
teaching: 10
exercises: 0
questions:
- How to connect to Sumhpc"
objectives:
- "Introduction to basic SLURM commands"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---


{% include links.md %}

### Directory Structure Best Practice

seff

sacct --brief

sacct -S2014-07-03-11:40 -E2014-07-03-12:00 -X -ojobid,start,end,state


sacct -T -S2014-07-03-11:40 -E2014-07-03-12:00 -X -ojobid,jobname,user,start,end,state

sacct --allocations

sacct -u <userid> -S 2020-02-25 format=User,JobID,Jobname,partition,state,time,start,end,elapsed,MaxRss,MaxVMSize,nnodes,ncpus,nodelist

