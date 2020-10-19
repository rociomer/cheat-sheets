### Useful commands for using [conda](https://docs.conda.io/projects/conda/)

To create a new environment:

```
conda create --name my-env-name
```

---

To create a new environment with a specific package:

```
conda create -n my-env-name pandas
```

---

To create an environment from a YML file:

```
conda env create -f path/to/environment.yml
```

---

To view a list of packages installed in an environment:

```
conda list -n my-env-name
```

---

To export an activated environment to a YML file:

```
conda env export > path/to/environment.yml
```

---

To delete an environment:

```
conda remove --name my-env-name --all
```
