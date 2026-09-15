# Running Jobs on Alpine

No we will learn how to run jobs on ALPINE.

For small jobs, we can run them on the command line as we would on our own terminal. Let's try this together.

**!!! Exercise together**

- Navigate to your scratch space on ALPINE and start a new project directory called DSCI510_demo

```
cd /scratch/alpine/$USER
$ pwd # make sure you are where you think you are
$ mkdir DSCI510_demo
$ cd DSCI510_demo
```

- Go back to the onDemand Dashboard and go to this same location in the **Files** window.

<p align="center">
<img width="410" alt="DSCI510_demo" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/DSCI510_demo.png">
</p>

- Return to the terminal, and start a job called `helloWorld.sh`

```
touch helloWorld.sh
```

- Now, switch back to the file open helloWorld.sh by pulling down the horizontal dot menu and selecting **Edit:**

<p align="center">
<img width="410" alt="script_edit_demo" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/scriptEditDemo.png">
</p>

- Write the following script:

```
#!/bin/usr/env bash
 
echo "Hello world!"
```

- Execute the script on the command line like so:

```
$ bash helloWorld.sh
```

Well, that sure seemed familiar. We can do this for simple tasks and scripts - things like copying files, moving files, and scripts that use very little time and hardware.

Once our jobs take longer to execute or require more processing power (cores), then we need to get in line by using the **job sharing utility** called **SLURM**.

### Using SLURM to submit jobs to the compute nodes

The job sharing utility that is installed on ALPINE is called **SLURM** and we use it by writing and executing **batch scripts**. batch scripts are just specialized bash scripts that are executed using the command `sbatch`. batch scripts do everything that bash scripts do, but in addition, they request a certain amount of the supercomputer for use and request a certain amount of time on that hardware. When we execute batch scripts, they don't run right away. Instead, they get in the queue and are assigned to a node based on the requested hardware, requested time, and availability.

- [Guide to running jobs using SLURM](https://curc.readthedocs.io/en/latest/running-jobs/batch-jobs.html)
- [SLURM guide](https://slurm.schedmd.com/sbatch.html)

To turn a bash script into an sbatch script we just need to do a few things …
1. change the file extension
2. add directives
3. execute with the command `$ sbatch <yourscript.sbatch>`

Our `.sh` script can be converted into an `.sbatch` script like so …

```
#!/bin/usr/env bash
 
## Directives go here...
#SBATCH <SLURM commands>
#SBATCH <SLURM commands>
#SBATCH <SLURM commands>
#SBATCH <SLURM commands>
#SBATCH <SLURM commands>
#SBATCH <SLURM commands>
 
## Software is loaded here...
module load <desired software>
 
## Your regular old shell script goes here...
echo "Hello World"
```

**!!! Exercise together:**

First, let's make a copy of our script `helloWorld.sh` called `helloWorld.sbatch`:

```
$ cp helloWorld.sh helloWorld.sbatch
```

Next, let's open this script in the text editor (edit in the file navigator window). Now, let's modify the code like so:

```
#!/usr/bin/env bash
 
#SBATCH --partition=atesting
#SBATCH --qos=testing
#SBATCH --nodes=1
#SBATCH --ntasks=1
#SBATCH --time=00:01:30
#SBATCH --output=sample-%j.out
 
# This will be a really slow way of printing out Hello World. The script will pause for 30 seconds after hello and after world.
echo "hello"
sleep 30
echo "world"
sleep 30
```

Don't forget to save your script

Let's execute this script like so from the terminal …

```
$ sbatch helloWorld.sbatch
$ squeue -u $USER   #Allows you to check on the status of your job
$ more sample*      #Check the progress of the outputfile
```

Explanation: What do the SBATCH Directives do?

```
#SBATCH --qos=testing <-- used for all testing partitions 
#SBATCH --nodes=1   <-- Requests 1 node
#SBATCH --ntasks=1  <-- Requests 1 core (can be up to 64 per single node)
#SBATCH --time=0:1:30   <-- Requests 1 minute & 30 seconds of time. Job will stop then
#SBATCH --partition=atesting  <-- Requests a "testing partition"
#SBATCH --output=sample-%j.out <-- saves the output in a file named sample-%j.out where %j is a variable where the job number will output
```

- [Learn more about SBATCH Directives](https://curc.readthedocs.io/en/latest/running-jobs/batch-jobs.html)
- [Learn more about Partitions](https://curc.readthedocs.io/en/latest/running-jobs/job-resources.html)

#### Useful SLURM commands

```
# To submit a job
$ sbatch <script.sbatch> 
 
# To check on all your currently running or requested jobs:
$ squeue -u $USER
 
# To see all your recent jobs:
$ sacct -u $USER
 
# To cancel a job:
$ scancel <job-id>
 
# My favorite output of job info:
$ sacct -X --format JobID,JobName,AllocCPUS,State,ExitCode,Elapsed,TimeLimit,Submit,Start,End
```

Continue on to [Next steps on Alpine](4-8_Next_Steps_on_Alpine.md)
