# Attestable's performance evaluation

This repository contains some experiments executed on Morello Board compartments to evaluate some of its performance parameters. Our final aim is to evaluate the cost of instantiating attestables in the Morello Board. For example, how many of them can be instantiated.


## Memory exhaustion by attestable replicas
The main aim of this experiment is to measure and analyse how the memory of a Morello Board is consumed by instances of attestables. To this end, we implemented 
a executable-program.c, compiled with library compartmentalisation tool and 
loaded in a compartment.  The metric to measure is the number of attestables
that can be created on a Morello Board before consuming 90% of its
memory. 

In addition to the number of attestables, we took the opportunity to collect metrics about the time it takes the operating sustem to wipe the memory used by the
attestable.

<p>
Some experimental facts:

1) The morello board used to conduct the experiment
   has 17118408704 bytes  (approximately 17.1 GB).
   
1) The computation of executable-program.c is irrelevant. In the experiments that we conducted, it executes some mathematical functions. It can be also the EAI
discussed in - [tee-compartimentalisation-study-case repository](https://github.com/CAMB-DSbD/tee-compartimentalisation-study-case "Git repository"). We compiled as shown below:

<p>
***$ clang-morello -march=morello+c64 -mabi=purecap***<br>     
  -g -o integration_process  integration_process.c -L.<br>     -Wl,-dynamic-linker,/libexec/ld-elf-c18n.so.1 
  -lssl -lcrypto -lpthread***<br>    
</p>

1) cheri-cap-experiment.py scrypt is used create the replicas of the attestables, and collect metrics. We incremented the number of replicas created from 1 to 3800.
See [replication of attestable results](https://github.com/CAMB-DSbD/tee-morello-performance-experiments/blob/main/cheri-caps-executable-performance/cheri-cap-experiment-results.csv "svs file")
</p>

 
<p>
The following figure shows the experiment set up.

<p align="center">
  <img src="./figures/create_load_atts.png"
   width="500" title="Create attestables to consume 90% of total memmory.">
</p>
</br>
</pr>


Imagine that user Alice is conducting the experiment. To created
the attestables and collect the metrics, Alice
executes the following steps:


1) Initiation: In the morello board Alice initiates cheri-cap-experiment.py.
 

1) Launch: to launch cheri-cap-experiment.py Alice executes
   % python3 cheri-cap-experiment.py

1) python3 cheri-cap-experiment.py runs incrementally creating attestable replicas until it detects that the attestables have 
consumed 90% of the 17118408704 bytes of the Morello Board's memory, that 
is, about 15406567833 bytes.


### Preliminary observations:
From the preliminary results 
(see [replication of attestable results](https://github.com/CAMB-DSbD/tee-morello-performance-experiments/blob/main/cheri-caps-executable-performance/cheri-cap-experiment-results.csv "svs file"))
it seems that 3800 compartments 
consume 90% of the Morello Board's memory. But this is only a
first glance observation that we will need to double
check to make a sound claim.
 
 
 
 ### Acknowledgements
 The code was mainly implemented mainly by Regis Rodolfo Schuch (regis.schuch@unijui.edu.br) <br>
  
 Member of the Applied Computing Research Group, Unijui University, Brazil




 ## Corresponding author  
 Carlos Molina-Jimenez (carlos.molina@cl.cam.ac.uk)   
 Computer Lab, University of Cambridge.

 
