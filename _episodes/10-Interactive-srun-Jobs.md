---
title: "10 Interactive SRUN Jobs"
teaching: 10
exercises: 0
questions:
- "How to run an interactive job with srun"
objectives:
- "Introduction to srun interactive jobs."
- "Introduction to setting slurm parameters."
- "Highlight the how program resource parameters still need to be set."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

{% include links.md %}

# Slurm **srun** Basics

## To get an interactive node with srun (no MPI)

- Default srun request **small tasks only** (1 hr time limit, 1 core, 1 GB, compute partition & batch QoS). \
```srun --pty bash```

- General format for srun [**do not execute without changing values**]\
```srun -p <partition> -q <QoS> -N <Number of Nodes> -n <Number of tasks> -c <cores> --time <time> --pty bash```

- Single-core srun interactive job on **dev** partition and **dev** QoS with 4 cpus and 8GB RAM for 4 hrs.\
```srun -p dev -q dev -N 1 -n 1 -c 1 --mem 8GB --time 4:00:00 --pty bash```

- Sing the **srun jingle** ... ```srun -p dev -q dev -N 1 -n 1 -c 1 --mem 10GB --pty bash```

- Additional examples for srun can be found here:
```https://github.com/TheJacksonLaboratory/slurm-templates```

## Hands on srun example

- Run srun:
```srun --pty bash```

- Notice the prompt changed to a specific node and is no longer the login node, this means your free to run programs (within your requested parameters). 

- 2 challenges to look around on the node. 

> ##  Look at the node CPU information
>
>Lets take a look at the CPU(s) information on the node using the ```lscpu``` command
>
>```
>$ lscpu 
>```
>{: .bash}
>
>> ## Result
>>```
>>Architecture:          x86_64
>>CPU op-mode(s):        32-bit, 64-bit
>>Byte Order:            Little Endian
>>CPU(s):                72
>>On-line CPU(s) list:   0-71
>>Thread(s) per core:    2
>>Core(s) per socket:    18
>>Socket(s):             2
>>NUMA node(s):          2
>>Vendor ID:             GenuineIntel
>>CPU family:            6
>>Model:                 85
>>Model name:            Intel(R) Xeon(R) Gold 6150 CPU @ 2.70GHz
>>Stepping:              4
>>CPU MHz:               1199.871
>>CPU max MHz:           3700.0000
>>CPU min MHz:           1200.0000
>>BogoMIPS:              5400.00
>>Virtualization:        VT-x
>>L1d cache:             32K
>>L1i cache:             32K
>>L2 cache:              1024K
>>L3 cache:              25344K
>>NUMA node0 CPU(s):     0-17,36-53
>>NUMA node1 CPU(s):     18-35,54-71
>>Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb cat_l3 cdp_l3 invpcid_single intel_ppin intel_pt ssbd mba ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm cqm mpx rdt_a avx512f avx512dq rdseed adx smap clflushopt clwb avx512cd avx512bw avx512vl xsaveopt xsavec xgetbv1 cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local dtherm ida arat pln pts pku ospke md_clear spec_ctrl intel_stibp flush_l1d
>>```
>>{: .bash}
>>{: .output}
>{: .solution}
{: .challenge}

- **Note** that you see all 72 CPUs (0-71) but you only requested 1 CPU (core), this is why it is important that NCPU parameters are set in scripts (e.g. R, python) and programs in addition to the srun and sbatch number of cpu parameters (-c). Some programs will look at the total number of CPUs, see all 72 these, and try to use all 72, although your not allocated all the CPUs. Setting the number of cpus in the srun/sbatch parameters **is not sufficient** for limiting the number of CPUs programs will try to access. Using more CPUs than allocated will impact other users any job seen doing this will be terminated.

> ##  Look at the Node Available RAM (Memory)
>
>Lets take a look at the available memory on the node using the ```free -h``` command
>
>```
>$ free -h 
>```
>{: .bash}
>
>> ## Result
>>```
>>              total        used        free      shared  buff/cache   available
>>Mem:           754G         16G        292G        789M        445G        734G
>>Swap:           63G        319M         63G
>>```
>>{: .bash}
>>{: .output}
>{: .solution}
{: .challenge}

- **Note** that you see all the MEM on the node but you only requested 1 GB, this is why it is important that you do not try to use more MEM that requested. Setting the MEM in the slurm parameters **is not sufficient** for limiting the amount of MEM a program will try to access. Using more MEM than allocated will impact other jobs any jobs seen doing this will be terminated.

- Now exit the interactive node with the ```exit``` command.

 - your prompt should change back to the login node. 
