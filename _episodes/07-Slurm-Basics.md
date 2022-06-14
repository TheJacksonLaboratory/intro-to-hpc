---
title: "07 Slurm Basics"
teaching: 15
exercises: 0
questions:
- "What is Slurm"
objectives:
- "Introduction to basic Slurm commands"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---
FIXME

{% include links.md %}

# General Slurm Usage and Commands

|  Usage               |              Slurm Commands                |
|----------------------|--------------------------------------------|
| submit job           | **srun**,    **sbatch**,    **salloc**     |
| view cluster status  | **squeue**,   **sinfo**                     |
| view cluster config  | '**scontrol** show partition' **sacctmgr** |
| view job information | **sacct**,     **seff**,     **sstat**     |
| cancel job           | '**scontrol** -f \<JobID\>'                |

**Slurm documentation** can be found here: LINK 

### Usage: Submitting Jobs to Slurm
- **srun** is the command for requesting an interactive job.

- **sbatch** is the command for requesting an batch job.

- **salloc** is another command for requesting an interactive job.

### Usage: Viewing the current status of cluster

- **squeue** shows the queue 

- **sinfo** shows the cluster partitions and node utilization

### Usage: View cluster config 
The commands below have multiple parts the whole command within the quotes should be executed. 

- '**scontrol** show partition' shows the partitions 

- '**sacctmgr** show qos format="name%-20,maxjobspu%-12,maxtrespu%-30,maxwall%-20"' shows the QoS quality of service

### Usage: View job information 
- **sacct** 

- **seff**

- **sstat**

### Usage: Cancel job
- '**scontrol** -f \<JobID\>' cancels job 

## Common Slurm Terms and Parameters For srun and sbatch

| Common Name            | - flag | -\-flag            |   Definition/notes                           |
|------------------------|--------|--------------------|----------------------------------------------|
| Account                | -A     | -\-account         |                                              |
| Array **(sbatch only)**| -a     | -\-array           | execute multiple jobs with one job request   |
| CPUsPerTask            | -c     | -\-cpus-per-task   | Usually set to number of CPUs/threads req.   |
| Dependency             | -d     | -\-dependency      | Make job execution dependent on previous job |
| Pass Variable          |        | -\-export          | Pass BASH variable to job                    |
| Print help             | -h     | -\-help            |                                              |
| Hold                   | -H     | -\-hold            | Queue job but do not run                     |
| JobName                | -J     | -\-job-name        | Set job name                                 |
| Memory                 |        | -\-mem             | Set memory (RAM) requirement for job         |
| Request specific nodes | -w     | -\-nodelist        |                                              |
| Number of nodes per job| -N     | -\-nodes           | Usually set to 1 (may vary w/advanced usage) |
| Number tasks per node  | -n     | -\-ntasks          | Usually set to 1 (may vary w/advanced usage) |
| Output                 | -o     | -\-output          |                                              |
| Partition              | -p     | -\-partition       |                                              |
| QOS                    | -q     | -\-qos             |                                              |
| Time Limit             | -t     | -\-time            | Set limit on job run time                    |


## Slurm Terms and Parameters For sacct 

| Common Name             | - flag | -\-flag            |   Definition/notes                           |
|-------------------------|--------|--------------------|----------------------------------------------|
| JobID                   | -j     | --jobs             | display information about job or jobs        |
| UserID                  | -u     |                    |                                              |
| Output Format           | -o     | --format           |                                              |
| Output Format help      | -e     | --helpformat       | Print a list of fields for --format option   |
| Output Format long style| -l     | --long             | long format option                           |
| Jobs included after     | -S     | --starttime        |                                              |
| Jobs included before    | -E     | --endtime          |                                              |
| UserID                  | -u     | --uid              |                                              |
| State of Jobs           | -s     | --state            |                                              |
| Nodes                   | -N     | --nodelist         | Print jobs ran on these nodes                |


## Usefull sacct format fields 

| Common Name   | Description                                                              |
|---------------|--------------------------------------------------------------------------|
| AllocCPUS     |                                                                          |
| AllocNodes    |                                                                          |
| CPUTime       |                                                                          |
| Elapsed       |                                                                          |
| JobID         | Jobs JobID                                                               |
| JobName       | Job Name                                                                 |
| MaxRSS        | Max Memory Used for job                                                  |
| UserID        |                                                                          |
| NCPUS         |                                                                          |
| Partition     | Partition requested                                                      |
| QOS           | QOS requested                                                            |
| ReqMem        | MEM requested                                                            |
| Start         | Start time of job                                                        |
| End           | End time of job                                                          |
| State         | State of job                                                             |
| ExitCode      | Exit code from job                                                       |


## HPC Live

[HPC Live](https://hpclive.jax.org/d/_yYwcFxZk/sumner-dashboard?orgId=2&refresh=5m)

