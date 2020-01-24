# Dockerbooks

Light(er) weight Jupyter Notebook docker images without conda.

Differences from Jupyter's docker stacks project:

- No Conda (why have Conda if I have Docker?).
- Lighter and smaller (Based on Python:3.7-slim).
- No annoying `jovyan` user that you always mispell and never notice.

## Usage:

User is `jupyter` and work directory for mounting:

```shell
-v "$PWD":/home/jupyter/work
```

Install extra python packages via pip with `--user` option:

``` shell
pip install --user foo
```
