---
title: "12 Batch Jobs with sbatch"
teaching: 10
exercises: 0
questions:
- "What are the advantages of sbatch over srun?"
- "How do I run a sbatch job?"
- "Where can I find example headers?"
- "How do I format sbatch headers?"
- "How do I capture the jobid?"
objectives:
- "Know how to format a sbatch script."
- "Know how to run a sbatch job."
- "Know how to capture the jobid."
- "Understand the usefulness of slurm arrays."
keypoints:
- "**sbatch** allows you to schedule jobs that will execute as soon as the requested resources are available."
- "Example headers can be found at https://github.com/TheJacksonLaboratory/slurm-templates "
- "Common slurm batch file extensions include ```.sh``` and ```.slurm``"
- "Save the job ID into a file with output redirect"
---

{% include links.md %}

# sbatch basics 

The Slurm sbatch header

```BASH
#!/bin/bash

#SBATCH --job-name=MY_JOB    # Set job name
#SBATCH --partition=dev      # Set the partition 
#SBATCH --qos=dev            # Set the QoS
#SBATCH --nodes=1            # Do not change unless you know what your doing (it set the nodes (do not change for non-mpi jobs))
#SBATCH --ntasks=1           # Do not change unless you know what your doing (it sets the number of tasks (do not change for non-mpi jobs))
#SBATCH --cpus-per-task=4    # Set the number of CPUs for task (change to number of CPU/threads utilized in run script/programs) [-p dev -q dev limited to 30 CPUs per node]
#SBATCH --mem=24GB           # Set to a value ~10-20% greater than max amount of memory the job will use (or ~6 GB per core, for dev) (limited to 180 GB per node on dev partition)
#SBATCH --time=8:00:00       # Set the max time limit (dev partition/QoS has 8 hr limit)

###-----load modules if needed-------###
module load singularity

###-----run script below this line-------###



```

- note the first line is the location of the bash executable 

- sbatch parameters are then set with the #SBATCH lines

- your code is entered in the black space below 'run script below this line'.

- common slurm batch file extensions include ```.sh``` and ```.slurm```. 

- Slurm documentation for sbatch can be found at https://slurm.schedmd.com/sbatch.html .

- Sumhpc example headers can be found at https://github.com/TheJacksonLaboratory/slurm-templates .

# Example

- Lets make a new directory (called 'adir') on fastscratch and navigate to it:\
```mkdir -p /fastscratch/${USER}/adir```\
```cd /fastscratch/${USER}/adir```

- Verify your in the correct directory:\
```pwd```

- Now grab the batch job templates:\
```git clone git@github.com:TheJacksonLaboratory/slurm-templates.git``` 

- Navigate into the new directory slurm-templates:\
```cd slurm-templates```

- Use ```cat``` to  view the template example `slurm_template_02_compute_batch.sh`:\
```cat slurm_template_02_compute_batch.sh``` 

- Navigate into the workshop examples: \
```cd workshop_examples``` 

- Use ```cat``` to view the workshop example `slurm_00_sleep_dev_dev.sh` :\
```cat slurm_00_sleep_dev_dev.sh ``` 

- Now before we submit the script, let's see if we are running anything else:\
```squeue -u ${USER} ```

- Note after we submit the script we can rerun ```squeue -u ${USER} ``` to see its running state: \

- Now submit the script with the ```sbatch``` command:\
```sbatch slurm_00_sleep_dev_dev.sh```

- You will get a job number printed to the screen: \

- Verify it is running with ```squeue -u ${USER} ```

- Now lets do it again but this time pipe the job id to a file so we have the jobid for later:\
```sbatch slurm_00_sleep_dev_dev.sh &> my_job_id.txt ```

- Notice nothing was printed to screen:\

- Verify it is running with ```squeue```:\
```squeue -u ${USER} ```

- View the jobid with cat:\
```cat my_job_id.txt ```


# Arrays are a useful extension to sbatch jobs 

- Arrays are extremely useful in parallelizing tasks that only change by 1 item. For example aligning multiple DNA fastq files with bwa. 

- Arrays are scheduled like 1 job but turn into multiple jobs as determined by the ```--array``` parameter, every element in the array parameter gets its on job. 

- Arrays jobs differ by the array element (a number) passed to the job script in the  ```${SLURM_ARRAY_TASK_ID}``` variable. 

- The ```${SLURM_ARRAY_TASK_ID}``` variable is used within the array's slurm script to vary the code within the script's parameters. 

- A common array method is to select a line of text from a text file from a list and assign it to a new variable:

```NEWVAR=$(sed -n -e "${SLURM_ARRAY_TASK_ID} p" /home/${USER}/my_important_list.txt)```

 - the list should be 1 item per line and be unix formatted


# Array examples

- View the example list ```list_lib_names.txt```: \
```cat list_lib_names.txt ```

- View the example sbatch array script ```slurm_01_array_dev_dev.sh```:  \
```cat slurm_01_array_dev_dev.sh ```

- View the content of our working directory:\
```ls ```

- Run the array job:\
```sbatch slurm_01_array_dev_dev.sh &> my_array_01_job_id.txt ```

- Verify it is running with ```squeue```.\
```squeue -u ${USER} ```

- View the jobid with cat.\
```cat my_array_01_job_id.txt ```

 - Note that the array only prints one jobid to the output, but many were viewed as running. \

- View array script output files:\
```ls ```

- View the output with cat.\
```cat array_run1_1_out_SRR2062637_file_names.txt ```

- Run the array job:\
```sbatch slurm_02_array_dev_dev.sh &> my_array_02_job_id.txt ```

- Verify it is running with ```squeue```.\
```squeue -u ${USER} ```

- View the output with cat.\
```cat array_run2_1_out_SRR2062637_file_names.txt ```


