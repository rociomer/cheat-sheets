### Useful commands for working with Jupyter notebooks

To start Jupyter, first load a conda environment where Jupyter is installed, then run:

```
$jupyter-lab
```
---

To open a remote Jupyter notebook using an SSH tunnel:

```
On remote machine, run:

$jupyter-lab --port 8857 --no-browser

On local machine, run:

$ssh -N -f -L localhost:8856:localhost:8857 user@ip.address

Then, open Jupyter Lab on the local machine by typing into any browser:

localhost:8856
```

The specific port numbers can be anything, the above is just an example.

---

To convert a Jupyter notebook to HTML:

```
$jupyter-nbconvert --to html path/to/file.ipynb
```
