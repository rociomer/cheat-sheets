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

To run an interactive session (example):

```
$srun -p gpu -c 4 --mem=28g -N 1 --gres=gpu:1 -t 7-00:00:00 --pty /bin/bash
```
