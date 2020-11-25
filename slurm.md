### Useful commands for working with SLURM                                                

To show quota on drive, type:

```
$module load quota
$show_quota
```

---

To check available GPUs:                              

```
nvidia-smi                                                                      
```

---

To monitor GPU usage:

```
nvidia-smi -l 1
```

The command above refreshes `nvidia-smi` every 1 second.

---

To run an interactive session (example):

```
$srun -p gpu -c 4 --mem=28g -N 1 --gres=gpu:1 -t 7-00:00:00 --pty /bin/bash
```

---

Example SLURM submission script for a GPU job:

```
#!/bin/bash
#SBATCH --job-name=my-job-name                # job name
#SBATCH --output=my-job-name.o${SLURM_JOB_ID} # write STDOUT to this file
#SBATCH --time=5:00:00                        # wall time dd-hh:mm:ss (dd = days, hh = hours, mm = minutes, ss = seconds)
#SBATCH --partition=gpu                       # -p, set the cluster partition to gpu
#SBATCH --nodes=1                             # -N, node count
#SBATCH --cpus-per-task=1                     # -c, cpu core count
#SBATCH --gres=gpu:1                          # specify use of a generic resource (single gpu)
#SBATCH --mem=50g                             # RAM requirement (on whichever type of specified node e.g. cpu or gpu)
                                                                                
# put commands for executing job below this line                                
export QT_QPA_PLATFORM='offscreen'            # for matplotlib backend
python my-python-script.py                    # example
```

---

To check the RAM usage of a job currently running (replace ${JOB_ID} with your job's ID):

```
sstat -j ${JOB_ID}.batch --format=AveRSS,MaxRSS,AveCPU
```

To check the RAM usage of a finished job (replace ${JOB_ID} with your job's ID):

```
sacct -o reqmem,elapsed,maxrss,averss -j ${JOB_ID}
```

In the above command, the following arguments are:
* reqmem = memory asked from slurm. Mn == MB per node, Mc == MB per core
* elapsed = time it took to run job
* maxrss = maximum amount of memory used at any time by any process in that job applies directly for serial jobs, but for parallel jobs, need to multiply by the number of cores
* averss = average memory used per process (or core), for total memory used multiply this with number of cores
