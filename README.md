# `isub` for the Palmetto Cluster

Script to make it easier to submit interactive jobs to Palmetto.

## Usage

Invoking `isub` with no arguments will give you a series of prompts where you
may enter your desired options.

```txt
bfgodfr@login002 ~ $ isub

How much walltime? [8:00:00]: 4:00:00
How many nodes? [1]:
How many CPU cores? [2]: 4
How much memory? [4gb]: 8
Which interconnect? [1g]:
How many GPUs? []:

+ qsub -I -l select=1:mem=8gb:interconnect=1g:ncpus=4,walltime=4:00:00
qsub (Warning): Interactive jobs will be treated as not rerunnable
qsub: waiting for job 422727.pbs02 to start
qsub: job 422727.pbs02 ready

bfgodfr@node0117 ~ $
```

### Resource Specification Flags

| Long Flag(s)                       | Short Flag | Description                          | Default |
| ---------------------------------- | ---------- | ------------------------------------ | ------- |
| `--select`                         | `-s`       | The numer of compute nodes.          | 1       |
| `--ncpus`<br>`--cores`<br>`--cpus` | `-c`       | The number of CPU cores.             | 2       |
| `--mem`<br>`--memory`              | `-m`       | The amount of memory, in GB.         | 4gb     |
| `--interconnect`                   | `-i`       | The interconnect type to use.        | 1g      |
| `--ngpus`<br>`--gpus`              | `-g`       | The number of GPU devices.           |         |
| `--gpu-model`                      | `-gm`      | The model of GPU to use.             |         |
| `--phase`                          | `-p`       | The phase of the cluster to land on. |         |

**NOTE:** Specifying any resource specification flags will disable the prompts
and accept defaults for any flags not passed. If you would like to prompt for
the remaining parameters instead, see `--ask` below.

### Other Flags

| Long Flag(s) | Short Flag | Description                                                      |
| ------------ | ---------- | ---------------------------------------------------------------- |
| `--ask`      | `-a`       | Ask for any parameters that are not defined with flags.          |
| `--default`  | `-d`       | Accept defaults and do not prompt.                               |
| `--explain`  | `-e`       | Before executing the `qsub` command, show what will be executed. |
