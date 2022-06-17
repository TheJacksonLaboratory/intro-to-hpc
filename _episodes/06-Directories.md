---
title: "06 Directories"
teaching: 20
exercises: 0
questions:
- "What does the directory structure look like in the Sumhpc environment?"
- "Where do I have space to store files?"
- "What is the fastscratch and why is it erased?"
- "How do I transfer files into and out of Sumhpc?"
- "Are there additional storage locations ?"
objectives:
- "Know the 3 writeable locations on Sumhpc: **/home/${USER}**, **/fastscratch**, **/projects**"
- 'Know files are removed from /fastscratch after 10 days.'
- 'Know that additional storage is located in on Tier2 and Tier3 (archive), but these are not directly accessible on the HPC system.'
- 'Know globus is used to transfer data into and out of the HPC environment'
keypoints:
- "The 3 writeable locations on Sumhpc: /home/${USER}, /fastscratch, /projects"
- 'Files are removed from /fastscratch after 10 days.'
- 'Faculty must approve access to their /projects directory.'
- "Good directory management can be helpful for organization. "
- "Globus is used to transfer data into and out of the HPC environment (see lesson 14)"
---

{% include links.md %}


## What you will need to know today 

- 3 main directories for working on Sumhpc: **/home/${USER}**, **/fastscratch**, **/projects**

- 4 Tiers are utilized for data management (2 of these are accessible via HPC)

## We utilize 4 Tiers of storage each optimized for specific role. 

| Tier | Mounted as                    | Backups? | Notes |
|------|-------------------------------|----------|----------------------------------------------|
|Tier0 | **/fastscratch**              | None     | shared space for temporary computational use |
|Tier1 | **/home**  &  **/projects**   | No*      | | 
|Tier2 | Not Mounted to HPC | Yes**    | Used for storing “cooler” data, not meant for HPC computations| 
|Tier3 | Not Mounted to HPC | Yes**    | Not accessible via Globus. Service desk ticket required for archival and retrieval.| 

\* Tier1 is not backed up but does have hidden .snapshot directory for recovery of deleted files within 7 days (this is not a true backup). \
\** Tiers 2 & 3 have cross-site replication between cross-site replication between BH and CT.
- globus is used to transfer between Tier2 and Tier1.

## We have 3 general locations (directories) we use for the HPC 

- ```/home/${USER}``` is the users home directory, every user is given 50 GB for their home directory.

- ```/fastscratch``` is a general working area for HPC data processing, data in this area is removed after 10 days. Total capacity 150TB

- ```/projects``` is the location where faculty store data and programs they use in there research programs, access to the PIs folders in ```/projects``` requires PI approval. 


>## Details and Suggestions for Directory Management for Your Review. 
>
> These are some suggestions for directory management 
>
>>### Directory Structure Best Practice
>>Time spent at the beginning of the project to define folder hierarchy and file naming conventions will make it much easier to keep things organized and findable, both throughout the project and after project completion. Adhering to well-thought out naming conventions:
>>
>>* helps prevent accidental overwrites or deletion
>>* makes it easier to locate specific data files
>>* makes collaborating on the same files less confusing
>>
>>### File naming best practices
>>
>>Include a few pieces of descriptive information in the filename, in a standard order, to make it clear what the file contains. For example, filenames could include:
>>
>>* experiment name or acronym
>>* researcher initials
>>* date data collected
>>* type of data
>>* conditions
>>* file version
>>* file extension for application-specific files
>>
>>#### Consider sort order:
>>
>>If it is useful for files to stay in chronological order, a good convention is to start file names with `YYYYMMDD` or `YYMMDD`.
>>
>>If you are using a sequential numbering system, use leading zeros to maintain sort order, e.g. `007` will sort before `700`.
>>
>>Do not use special (i.e. non-alphanumeric) characters in names such as:  
>>```" / \ : * ? ‘ < > [ ] [ ] { }  ( ) & $ ~ ! @ #  % ^   , '```
>>
>>These could be interpreted by programs or operating systems in unexpected ways.
>>
>>Do not use spaces in file or folder names, as some operating systems will not recognize them and you will need to enclose them in quotation marks to reference them in scripts and programs. Alternatives to spaces in filenames:
>>
>>* Underscores, e.g. file_name.xxx
>>* Dashes, e.g. file-name.xxx
>>* No separation, e.g. filename.xxx
>>* Camel case, where the first letter of each section of text is capitalized, e.g. FileName.xxx
>>* Keep names short, no more than 25 characters.
>>
>>### File Versioning Best Practices
>>
>>File versioning ensures that you always understand what version of a file you are working with, and what are the working and final versions of files. Recommended file versioning practices:
>>
>>* Include a version number at the end of the file name such as v01. Change this version number each time the file is saved.
>>* For the final version, substitute the word FINAL for the version number.
>>* Take advantage of the versioning capabilities available in collaborative workspaces such as github OSF, Google Drive, and Box.
>>* Track versions of computer code with versioning software such as Git, Subversion, or CVS.
>>
>>### Directory Structure Best Practices
>>Directories can be organized in many different ways. Consider what makes sense for your project and research team, and how people new to the project might look for files.
>>
>>Once you determine how you want your directories to be organized, it is a good idea to stub out an empty directory structure to hold future data, and to document the contents of each directory in a readme file.
>>
>>Directory Best Practices
>>
>>* Organize directories hierarchically, with broader topics at the top level of the hierarchy and more specific topics lower in the structure.
>>* Group files of similar information together in a single directory.
>>* Name directories after aspects of the project rather than after the names of individual researchers.
>>* Once you have decided on a directory structure, follow it consistently and audit it periodically.
>>* Separate ongoing and completed work.
>>
>>### Sources
>>http://guides.lib.umich.edu/datamanagement/files
>>
>{: .solution}
{: .challenge}