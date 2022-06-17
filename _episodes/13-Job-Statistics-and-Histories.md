---
title: "13 Job Statistics and Histories"
teaching: 10
exercises: 0
questions:
- "What types of historical information is available for my jobs?"
objectives:
- "Understand how to use seff and sacct"
keypoints:
- "sacct shows details on memory utilization (MaxRSS), but only for completed jobs."
---

{% include links.md %}

### Use ```seff``` to view information about a particular job.
 
 - ```seff``` usage: ```seff <jobid>```
 - requires jobid
 - Get previous jobid from output file:\
 ```ls ```
 - Run seff with jobid.\
```seff <jobid>```

### Use ```sacct``` to view more information for more jobs:\
```sacct -u ${USER} -S 2022-06-17 -oUser,JobID,Jobname,partition,state,time,start,end,elapsed,MaxRss,MaxVMSize,nnodes,ncpus,CPUTime,nodelist```

