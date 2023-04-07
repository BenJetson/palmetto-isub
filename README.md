# palmetto-isub
Script to make it easier to submit interactive jobs to Palmetto.

## Usage

Invoking `isub` with no arguments will give you a series of prompts where
you may enter your desired options.

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

### Resource Specification Arguments

### Other Arguments


