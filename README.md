# Dockerbooks

Light(er) weight Jupyter Notebook docker images without conda.

Differences from Jupyter's docker stacks project:

- No Conda (why have Conda if I have Docker?).
- Lighter and smaller (Based on Python:3.8-slim, scipy is < 1GB, pyspark is 2.7GB).
- No annoying `jovyan` user that you always mispell and never notice (instead, the user is `jupyter`).

## Images

Hosted on DockerHub, you can find images [here](https://hub.docker.com/orgs/dockerbooks/repositories).

* **dockerbooks/base** Base notebook, nothing but Jupyter.
* **dockerbooks/scipy** Extends base. Pandas/Numpy/Numba/Scikit-learn/Seaborn.
* **dockerbooks/pyspark** Extends scipy. Pyspark (Change the version in one line!).

## Usage:

User is `jupyter` and work directory for mounting:

```shell
-v "$PWD":/home/jupyter/work
```

Install extra python packages via pip with `--user` option:

``` shell
pip install --user foo
```
