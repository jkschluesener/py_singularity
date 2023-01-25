# Python Singularity Container

[Singularity](https://docs.sylabs.io/guides/3.5/user-guide/index.html) container definition to run a defined Python environment.  
Define public and private packages using conda and pip.

Singularity is intended for use on [HPC](https://en.wikipedia.org/wiki/High-performance_computing) infrastructure as opposed to Docker, which requires a root process.

## Customization

### Anaconda Packages

You can define your Python environment, including the Python version, in `conda/requirements.txt`. You will probably want to specify package versions. These packages need to be available on [Anaconda](https://anaconda.org/anaconda).

Note that complex environments may take quite some time to solve. This container uses [Mamba](https://github.com/mamba-org/mamba) for a speedup during the package install step of the container build process.

### PyPi and Private Packages

If you want to install packages from the [Python Package Index](https://pypi.org/), or from a local path for private packages, list them in `pip/requirements.txt`. Local packages need to be prefixed with `./`.

## Building the Container

```bash
sudo singularity build container.sif container.def
```

## Starting the container

```bash
singularity shell container.sif
```

## Running Python Applications

To launch e.g. `spyder`, run the following:

```bash
singularity container.sif /opt/miniconda3/bin/spyder
```

### Running Python Scripts

Run a python script without directly interacting with the container

```bash
singularity exec container.sif /opt/miniconda3/bin/python script.py
```
