---
title: "04 What is a Job"
teaching: 5
exercises: 0
questions:
- "What is a job?"
objectives:
- "Understand the difference in running jobs locally and on HPC system."
- "Understand what function a job serves in the HPC environment."
keypoints:
- "Understand the difference in running jobs locally and on HPC system."
- "Understand what function a job serves in the hpc environment."
---

{% include links.md %}

## A job 

- Accessing HPC cluster resources requires requesting them from a scheduler.
- Our scheduler is Slurm, other institution may use another scheduler. 
- A successful request (via srun or sbatch) to the scheduler creates a job.
- This job is appended to the queue and is executed once resources become available (sometimes immediately).
- The job is then transferred to the resources and executed (shell script for sbatch or terminal for srun).
