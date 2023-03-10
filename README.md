# Network_expansion
The following repository contain two functions needed for the network expansion method as descibed in doi: https://doi.org/10.1101/2021.07.19.452924 

This repository is divided in the following folders:
Rscripts: all needed scripts that run in R (base R plus igraph and pROC libraries)
Tables_expansion: all input and output for all the analysis (excluding the IBD section)
Tables_IBD: all input and output needed for the IBD-scpedific network analysis
Description concerning all RScripts:
Script_1_SEED.R: script meant to run in the cluster inside a loop, it runs the network expansion (once per trait) and score the resulting modules (see methods). 
Script_2_SEED.R: script meant to run in the cluster inside a loop, it does the benchmark of the Personalized Pagerank (PPR) scores (see paper).
Script_3_1.R: it calculates correlations and distances among traits using the PPR score with and without normalizations (Zscore). It also joints all the PPRs across traits
Script_3_2.R: script to joint all output tables from Script_1_SEED.R “
Script_4.R: it calculates the gene overlap among significant modules using jaccard index.
Script_5.R: it calculates jaccard indexes of trait ancestries (EFO) to use as benchmark for trait to trait distances.
Script_IBD_set1_SEED.R: modify network expansion for the IBD analysis using the curated list. 
Script_IBD_set2_SEED.R: modify network expansion for the IBD analysis using the L2G score list.

Barrio-Hernandez and colleagues used interaction data from the Open Targets platform to implement their method of network expansion
(Ref: https://github.com/saezlab/OTAR-BioCypher)
(https://www.biorxiv.org/content/10.1101/2021.07.19.452924v1). A dump file of the Neo4j knowledge graph they used is available at http://ftp.ebi.ac.uk/pub/databases/intact/various/ot_graphdb/current/.

Once successfully installed, porting the OTAR graph can be attempted by running a local (or remotely accesssible) instance of the OTAR graph dump in Neo4j and executing the Python script at scripts/barrio_hernandez_script.py. This will connect to BioCypher using the adapter (from adapters/barrio_hernandez_adapter.py) and write the BioCypher-compatible structured data to the biocypher-out directory. You can find a version of the neo4j-admin import command for the processed data in each individual output folder, under the file name neo4j-admin-import-call.sh, which simply needs to be executed in the home directory of the target database. More information about the BioCypher package can be found at https://biocypher.org.
