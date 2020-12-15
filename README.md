# species-notebooks

Polynote notebooks for Cross-Species transcriptomics project.
The repository contains part of preprocessing scripts for Cross-Species database and "Machine learning analysis of longevity-associated gene expression landscapes in mammals" paper.

The notebooks are divided into 3 folders:
* ensembl
* graphdb
* tables

ensembl
-------

In the ensembl folder there are notebooks to download all ensembl assemblies for vertebrates and notebook to convert transcripts to genes (as native sample transcript to gene conversion has bugs)

graphdb
-------
Code required to move gene expression values as well as orthology compara database to GraphDB

tables
------
To write .tsv tables with expressions of orthologous genes for further analysis

saparate notebooks
------------------
samples - to work with sample annotations
transcript_to_uniprot - for conversions of the transcripts to genes and then to uniprot ids of transcripted and then translated proteins
structural - helper methods to download proteins sequences by ids and for other stuff


Setting things up
-----------------

The project uses Scala 2.12.12, Polynote 0.3.12 and Spark 3.0.1 
You can set it up yourself or use corresponding docker container (i.e. quay.io/comp-bio-aging/polynote:master)
In the project we also assume the following directory structure 
(that can be changed by changing corresponding variables):
* /data/ensembl/<release> - for downloaded ensembl data
* /data/indexes/salmon/<version>/ensembl_<ensembl_release>/ - for indexes folders
* /data/databases/graphdb - for GraphDB
* /data/samples/species - for cross-species samples

NOTE: for reproducing results for longevity-associated gene expression landscapes in mammals paper it is enough to use https://github.com/antonkulaga/yspecies as it contains DVC-controled data. This repository is needed only if you want to requantify raw data with the latest version of ensembl or setup a graph database with cross-species genes expressions