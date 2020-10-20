### Useful commands for working with Python

To profile code using [cProfile](https://docs.python.org/3/library/profile.html#module-cProfile), run your code as follows:

```
python -m cProfile -o output-file-name.prof path/to/script.py
```

Then, you can visualize the output from cProfile using [snakeviz](https://jiffyclub.github.io/snakeviz/): 

```
snakeviz output-file-name.prof
```

The above command should open a browser window.

---

Another useful tool for debugging bottlenecks in a program is [torch.utils.bottleneck](https://pytorch.org/docs/stable/bottleneck.html). To use it, simply run (from within an environment that has torch installed):

```
python -m torch.utils.bottleneck path/to/script.py
```

---

To specifically profile memory usage, one good option is [memory-profiler](https://pypi.org/project/memory-profiler/).
