# Attestable's performance evaluation

This repository contains some experiments executed on Morello Board compartments to evaluate some of its performance parameters. Our final aim is to evaluate the cost of instantiating attestables in the Morello Board. For example, how many of them can be instantiated.


## Memory exhaustion by attestable replicas
The main aim of this experiment is to measure and analyse how the memory of a Morello Board is consumed by instances of attestables. To this end, we implemented 
a executable-program.c, compiled with library compartmentalisation tool and 
loaded in a compartment.  The metric to measure is the number of attestables
that can be created on a Morello Board before consuming 80% of its
memory. 

In addition to the number of attestables, we took the opportunity to collect metrics about the time it takes the operating sustem to wipe the memory used by the
attestable.


Some experimental facts:

1) The morello board used to conduct the experiment
   has 17118408704 bytes  (approximately 17.1 GB).
   
1) The computation of executable-program.c is irrelevant. In the experiments that we conducted, it executes some mathematical functions. It can be also the EAI
discussed in - [tee-compartimentalisation-study-case repository](https://github.com/CAMB-DSbD/tee-compartimentalisation-study-case "Git repository")

1) cheri-cap-experiment.py scrypt is used create the replicas of the attestables, and collect metrics. We incremented the number of replicas created from 1 to 8991.
See [replication of attestable results](https://github.com/CAMB-DSbD/tee-morello-performance-experiments/blob/main/cheri-caps-executable-performance/cheri-cap-experiment-results.csv "svs file")


Imagine that user Alice is conducting the experiment. To created
the attestables and collect the metrics, Alice
executes the following steps:


1) Initiation: In the morello board Alice initiates cheri-cap-experiment.py with the
following paremeters.

    a) process_list: list to store the processes started. For
     example Alice can type .....  in .... [where?]

    b) max_memory_usage: gets the total amount of memory available on the system.
     Alice .....??????

    c) csv_file: name of the CSV file to save the results. For
       example can chose results.csv

    d) elapsed) start_time: marks the start time to calculate the elapsed time.
       Alice .....?????

1) Launch: to launch cheri-cap-experiment.py Alice executes
   % python3 cheri-cap-experiment.py

1) python3 cheri-cap-experiment.py runs incrementally creating attestable replicas until it detects that the attestables have 
consumed 90% of the 17118408704 bytes of the Morello Board's memory, that 
is, about 15406567833 bytes.


### Preliminary observations:
From the preliminary results it seems that 3800 compartments 
consume 90% of the Morello Board's memory. But this is only a
first glance observation that we will need to double
check to make a sound claim.
 
 
