### Useful commands for working with SLURM                                                

SLURM is workload manager for Linux. SLURM commands all start with the letter *s*, e.g. `sinfo`, `sacct`, `squeue`.

---

#### Commands for checking the node status

Check which nodes are available by typing (from the login node)

```
sinfo
```

A list of all nodes available on the cluster will come up, generally divided by partition (e.g. CPU or GPU). This command is useful when you need to check the status of a specific node or partition.

---

#### Commands for running jobs

You can run two types of SLURM jobs: *interactive* or *batch* jobs. Interactive jobs are helpful when you need to run many small/quick jobs in succession, or are testing code (although, a cluster could also have a dedicated debug queue or node). However, you can also use interactive sessions for large jobs. Batch jobs are useful when you need to run many large jobs which don't really depend on each other.

To run an interactive job, you use the `srun` command in SLURM, whereas to run a batch job, you use the `sbatch` command. Below are more details on how to run each specific  job type.

To run a batch job, you would first need to create a submission script (e.g. *submit.sh*), which you can then submit as follows:

```
sbatch submit.sh
```

As an example of what such a submission script could look like, below is an example SLURM submission script for a GPU job that will run with a 5 hour time limit on a single node and is requesting 10 GB RAM, with some details on what each lines means:

```
#!/bin/bash
#SBATCH --job-name=my-job-name                # job name
#SBATCH --output=my-job-name.o${SLURM_JOB_ID} # write STDOUT to this file
#SBATCH --time=0-05:00:00                     # wall time format is dd-hh:mm:ss (dd = days, hh = hours, mm = minutes, ss = seconds)
#SBATCH --partition=gpu                       # -p, set the cluster partition to gpu
#SBATCH --nodes=1                             # -N, node count
#SBATCH --cpus-per-task=1                     # -c, cpu core count
#SBATCH --gres=gpu:1                          # specify use of a generic resource (single gpu)
#SBATCH --mem=10g                             # RAM requirement (on whichever type of specified node e.g. cpu or gpu)
                                                                                
# put commands to run on the requested node below this line                                
export QT_QPA_PLATFORM='offscreen'            # for matplotlib backend
python example.py                             # example
```

Alternatively, to request the same resources for an interactive session on a GPU, you would type into the terminal:

```
srun -p gpu -c 1 --mem=10g -N 1 --gres=gpu:1 -t 0-05:00:00 --pty /bin/bash
```


Note that it is not good practice to request a lot more resources than what you expect your job to use, as this will not only make it more difficult for you to get the resources you are requesting (e.g. longer queue time, depending on how many nodes are available and how many users are trying to use them), but also you are potentially blocking resources from others.

Interactive sessions are greate during development, but if you have many large jobs to run, it is probably better to submit them as batch jobs.

---

#### Commands for checking things

To check the status of any jobs you have submitted to the queue, type:

```
squeue -u <your username>
```

You could also simply type `squeue` but this is not usually a good idea, as it will return a list of all jobs running on the cluster.


To cancel a job, type:

```
scancel <job ID>
```


To show the quota on the drive, type:

```
module load quota
show_quota
```


To check available GPUs on a specific node, type:                              

```
nvidia-smi                                                                      
```


To monitor GPU usage on a specific node, type:

```
nvidia-smi -l 1
```

The command above refreshes `nvidia-smi` every 1 second.


To check the RAM of a job currently running (replace <job ID> with your job's ID):

```
sstat -j <job ID>.batch --format=AveRSS,MaxRSS,AveCPU
```

To check the RAM of a finished job:

```
sacct -o reqmem,elapsed,maxrss,averss -j <job ID>
```

In the above command, the following arguments are:
* reqmem = memory asked from slurm. Mn == MB per node, Mc == MB per core
* elapsed = time it took to run job
* maxrss = maximum amount of memory used at any time by any process in that job applies directly for serial jobs, but for parallel jobs, need to multiply by the number of cores
* averss = average memory used per process (or core), for total memory used multiply this with number of cores


Note that there are also many variables that you can use with SLURM, such as *${SLURM_JOB_ID}*, which will contain the job ID for a given job (see, for example, how I use it in *submit.sh*).
