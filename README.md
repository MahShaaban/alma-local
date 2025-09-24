TODO:

- [X] Implement slurm cluster
- [X] Shared volumns
- [ ] Add modules
- [ ] Replicate environment: Volumns and variables

# Test

Enter the `slurmmaster` shell first using

```bash
docker exec -it rancavil/slurm-master:19.05.5-1 bash
```

Otherwise, if working in a VS code dev, run

```console
$ cd test/

$ sinfo
PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
slurmpar*    up   infinite      3   idle slurmnode[1-3]

$ sbatch job.sh
Submitted batch job 3
admin@slurmmaster:~/test$ squeue 
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
                 3  slurmpar     test    admin  R       0:03      1 slurmnode1

$ ls
job.sh  result.out  test.py

$ more result.out
Process started 2025-09-24 08:35:40.172291
NODE : slurmnode1
PID  : 120
Executing for 15 secs
Process finished 2025-09-24 08:35:55.188293

Process started 2025-09-24 08:35:40.198770
NODE : slurmnode1
PID  : 116
Executing for 15 secs
Process finished 2025-09-24 08:35:55.203335

Process started 2025-09-24 08:35:40.211637
NODE : slurmnode1
PID  : 115
Executing for 15 secs
Process finished 2025-09-24 08:35:55.227651

Process started 2025-09-24 08:35:40.251085
NODE : slurmnode1
PID  : 118
Executing for 15 secs
Process finished 2025-09-24 08:35:55.267447

Process started 2025-09-24 08:35:40.295267
NODE : slurmnode1
PID  : 117
Executing for 15 secs
Process finished 2025-09-24 08:35:55.311495

Process started 2025-09-24 08:35:40.311047
NODE : slurmnode1
PID  : 119
Executing for 15 secs
Process finished 2025-09-24 08:35:55.315433
```

# Local build

```bash
docker compose -f docker-compose-jupyter.yml
```