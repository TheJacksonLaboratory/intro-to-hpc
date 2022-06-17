---
title: "09 Sumhpc Slurm Configuration"
teaching: 10
exercises: 0
questions:
- "How is Sumhpc configured with Slurm"
- "How do partitions, QoS, and user set parameters work together?"
objectives:
- "Understand how partitions, QoS, and user set parameters work together"
keypoints:
- "Partitions are sets of nodes with specific hardware configurations."
- "QoS are limits to resource (it is a shared systems)."
- "Users also set specific parameters so the resources allocated by the scheduler match what is needed."
- "Job queue wait times are optimized when slurm configuration parameters are optimal for job."
---

{% include links.md %}

## A Layer Model to Slurm Configuration (build from bottom up)

| Layer     | SLURM TERM          | Example(s)                 | Notes                                                           |
|:----------|:-------------------:|:--------------------------:|:---------------------------------------------------------------:|
| Layer 4   | user set parameters | -N, -n, -c, -\-mem -\-time | user defines what they need for particular job                  |
| Layer 3   | GRES                | -                          | optional, GPU cluster only for now, not needed for intro-to-hpc |
| Layer 2   | QoS                 | batch, long, dev           | user limits set by cluster administration                       |
| Layer 1   | Partition           | compute, dev, high_mem     | the hardware (based upon hardware properties)                   |


- Partition is the set of Nodes you would like to run on. 
- There is a partition named ```dev``` and a QoS named ```dev```.  
- QoS is administrative limits to the job, you can pick what QoS (set of limits) work best for your job.
- GRES (optional, GPU cluster only for now, not needed for intro-to-hpc)
- User provided configuration (-N/--nodes, -c)

### Sumhpc's Partitions 

|                        | compute     | high_mem   | dev             |
|:-----------------------|:-----------:|:----------:|:---------------:|
| # of nodes             | 100         | 2          | 20              |
| Usable memory per node | 754GB       | 3022GB*    | 180GB           |
| Usable cores per node  | 70          | 142        | 30              |
| CPU core speed​​​​​​​         | 2.70GHz     | 2.70GHz    | 3.60GHz         |
| Total partition MEM    | 76T         | 6T         | 3.6T            |
| Total partition cores  | 7000        | 284        | 600             |
| MaxTime                | 14-00:00:00 | 3-00:00:00 | 8:00:00         | 
| how to use?            | -p compute  | -p high_mem| -p dev & -q dev |


### Sumhpc's QoS.

|                                     | batch             |  long      | dev             |
|:------------------------------------|:-----------------:|:----------:|:---------------:|
| Max Wallltime per job               | 3 days            | 14 days    | 8 hours         |
| Default Walltime (if not specified) | 1 hour            | 1 hour     | 1 hour          |
| Max CPU per user                    | 700 cores         | 140 cores  | 60 cores        |
| Default CPU (if not specified)      | 1 core            | 1 core     | 1 core          |
| Max Memory per user                 | 7.6TB             | 1TB        | 360GB           |
| Default Memory (if not specified)   | 1GB               | 1GB        | 1GB             |
| Max running jobs per user           | 700               | 10         | 60              |
| how to use?                         | -q batch          | -q long    | -p dev & -q dev |
| Partitions Allowed On               | compute, high_mem | compute, \*| dev             |

\* ```long``` QoS is currently allowed on high_mem, but the high_mem partition only allows jobs to run for 3-00:00:00 (72 hr), so just use ```batch``` QoS. Also, ```long``` QoS is limited to 1TB RAM. 

- Only certain QoS's are allowed on specific partitions. 
 - **```compute```** partition only allows ```long``` and ```batch``` QoS.
 - **```dev```** partition only allows ```dev``` QoS.
    
## Important srun and sbatch parameters these are set per job.

| Common Name            | - flag | -\-flag            |   Definition/notes                           |
|------------------------|--------|--------------------|----------------------------------------------|
| CPUsPerTask            | -c     | -\-cpus-per-task   | Usually set to number of CPUs/threads req.   |
| Memory                 |        | -\-mem             | Set memory (RAM) requirement for job         |
| Request specific nodes | -w     | -\-nodelist        |                                              |
| Partition              | -p     | -\-partition       |                                              |
| QOS                    | -q     | -\-qos             |                                              |
| Number of nodes per job| -N     | -\-nodes           | Usually set to 1 (may vary w/advanced usage) |
| Number tasks per node  | -n     | -\-ntasks          | Usually set to 1 (may vary w/advanced usage) |
| Time Limit             | -t     | -\-time            | Set limit on job run time                    |

- we usually set the number of nodes to 1 for each job, but we can run multiple jobs at at time 