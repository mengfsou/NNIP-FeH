The Neural Network Interatomic Potential (NNIP) for $alpha$-Fe-H binary system

There are 3 folders:

1. DATABASE

The files of database.tar.gz0, database.tar.gz1,database.tar.gz2 (the 3 tar.gz files should be one file, we have to split it into 3 parts because of the size limitation of github) are the DFT database used for the construction of this NNIP.
Details of the database, please refer the paper of Phys. Rev. Mater.:Year,  Vol,  Pages, .. (doi:          )

The NNIP can be reproduced by:
 
 a. setup n2p2 package, please refer:  https://compphysvienna.github.io/n2p2/index.html
 
 b. extract and combine the files of database.tar.gz0, database.tar.gz1,database.tar.gz2, by typing: 
 
        cat database.tar.gz* | tar -zxv    , and
        
        mv database.data input.data (input.data is the name required by n2p2 package)
        
 c. using the input.nn file in the POTENTIAL folder and the above input.data file, performing training operation. 
    Details of training, please refer:  https://compphysvienna.github.io/n2p2/topics/training.html
 
2. POTENTIAL

The NNIP includes 4 files, input.nn, scaling.data, weights.001.data, and weights.026.data.
All these 4 files should be in one folder, and the setting in the LAMMPS input file is: 

pair_style      nnp     dir  ~/dir/to/the/POTENTAIL/folder
 
The interface of n2p2 and LAMMPS code, please refer:

https://compphysvienna.github.io/n2p2/interfaces/if_lammps.html
 
Deatails of the setting of pair_style, please refer: 

https://compphysvienna.github.io/n2p2/interfaces/pair_nnp.html

* lammps-n2p2 interface has been included in the Lammps package, please refer:

https://docs.lammps.org/pair_hdnnp.html

----------------------
pair_style      hdnnp   6.5  dir ${pot} showew no showewsum 1000 resetew yes maxew 10000 cflength 1.8897261328 cfenergy 0.0367493254

pair_coeff * *  H Fe

mass    1       1.008

mass    2       55.847

------------------------

3. EXAMPLE

An example for the application of NNIP in LAMMPS code.

NOTE: pair_style part used in this example is the old version!! 

---------end-----------
MOV.S1.avi and MOV.S1.avi are the movies mentioned in the supplemental materials of paper: 
DOI: 10.1103/PhysRevMaterials.5.113606

