# species-notebooks

Polynote notebooks for Cross-Species transcriptomics project.
The repository contains part of preprocessing scripts for Cross-Species database and "Machine learning analysis of longevity-associated gene expression landscapes in mammals" paper.
This repository needed if you want to requantify the data or add additional samples.
To reproduce the analysis of the paper with already quantified data [yspecies](https://github.com/antonkulaga/yspecies) repository should be used instead.

## Role of this repository in cross-species machine learning pipeline ##

![Cross-species Machine learning pipeline](/data/images/pipeline.png?raw=true "Machine learning pipeline in the paper")

On this figure we illustrate the core elements of the Cross-Species ML pipeline:

### RNA-quantification ###
For downloading and preparing the indexes of reference genomes and transcriptomes current [species-notebooks](https://github.com/antonkulaga/species-notebooks) repository can be used.

For RNA-Seq processing of samples [quantification](https://github.com/antonkulaga/rna-seq/tree/master/pipelines/quantification) pipeline can be used.

For uploading the data to GRAPHDB database current [species-notebooks](https://github.com/antonkulaga/species-notebooks) repository can be used.

### LightGBM+SHAP stages I, II, III models and ranked results###

To reproduce most of the models [yspecies](https://github.com/antonkulaga/yspecies) repository can be used (see its documentation)

### Other models ###

Linear models are implemented in [cross-species-linear-models](https://github.com/ursueugen/cross-species-linear-models) repository
Bayesian networks analysis and multilevel Bayesian linear modelling are available at: [bayesian_networks_and_bayesian_linear_modeling](https://github.com/rodguinea/bayesian_networks_and_bayesian_linear_modeling) repository

If you just need results you can pull them by [DVC](https://dvc.org) in [yspecies](https://github.com/antonkulaga/yspecies) repository

# Structure of  thespecies-notebooks repository #

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