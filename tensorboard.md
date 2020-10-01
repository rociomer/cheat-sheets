### Useful commands for using [Tensorboard](https://www.tensorflow.org/tensorboard)

To open a remote Tensorboard session on a local machine using an SSH tunnel:

```
From local machine, run:

$ssh -N -f -L localhost:8856:localhost:8857 user@ip.address

From remote machine, run:

$tensorboard --logdir path/to/log --port 8857

where the path points to a specific tensorboard session.

Then, to open the session on the local machine, type into any browser:

localhost:8856
```
