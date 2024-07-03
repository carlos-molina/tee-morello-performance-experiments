# Attestable's performance evaluation

This repository contains some experiments executed on Morello Board compartments to evaluate some of its performance parameters. Our final aim is to evaluate the cost of instantiating attestables in the Morello Board. For example, how many of them can be instantiated.


## Memory
The aim of this experiment is to measure and analyse memory
consumed by instances of an executable
program written in ..... [language, C | Python] and called ./executable-program.

Executable-program is run by ..... [who deployes] in .....
[morello | compartment created in morello]
and computes the function .....

The morello board used to conduct the experiment
has 17118408704 bytes  (approximately 17.1 GB)

To run the program and collect the metrics the user
Alice executed the following steps:


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

1) python3 cheri-cap-experiment.py runs till ...?


### Preliminary observations:
The results show that the number of instannces of ./executable-program
 


