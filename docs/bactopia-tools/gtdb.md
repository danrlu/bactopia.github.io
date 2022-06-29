---
tags:
---



# Bactopia Tool - `gtdb`
The `gtdb` tool uses [GTDB-Tk's](https://github.com/Ecogenomics/GTDBTk) classify 
workflow to assign taxonomic classifications to your set of samples. This is 
done through the use of the [Genome Taxonomy Database](https://gtdb.ecogenomic.org/). 
If you are unsure of your sequences, `gtdb` is useful tool to help determine
the taxonomy of your samples.


## Example Usage
```
bactopia --wf gtdb \
  --bactopia /path/to/your/bactopia/results \ 
  --include includes.txt  
```

## Output Overview

Below is the default output structure for the `gtdb` tool. Where possible the 
file descriptions below were modified from a tools description.

```{bash}
gtdb/
├── bactopia-info
│   ├── gtdb-report.html
│   ├── gtdb-timeline.html
│   └── gtdb-trace.txt
└── classify
    ├── align
    │   ├── gtdb.(ar122|bac120).filtered.tsv
    │   ├── gtdb.(ar122|bac120).msa.fasta
    │   ├── gtdb.(ar122|bac120).user_msa.fasta
    │   └── intermediate_results
    │       └── gtdb.(ar122|bac120).marker_info.tsv
    ├── classify
    │   ├── gtdb.(ar122|bac120).classify.tree
    │   ├── gtdb.(ar122|bac120).summary.tsv
    │   └── intermediate_results
    │       ├── gtdb.(ar122|bac120).classification_pplacer.tsv
    │       ├── gtdb.(ar122|bac120).red_dictionary.tsv
    │       └── pplacer
    │           ├── pplacer.(ar122|bac120).json
    │           └── pplacer.(ar122|bac120).out
    ├── gtdb.(ar122|bac120).classify.tree
    ├── gtdb.(ar122|bac120).filtered.tsv
    ├── gtdb.(ar122|bac120).markers_summary.tsv
    ├── gtdb.(ar122|bac120).msa.fasta
    ├── gtdb.(ar122|bac120).summary.tsv
    ├── gtdb.(ar122|bac120).user_msa.fasta
    ├── gtdb.translation_table_summary.tsv
    └── identify
        └── intermediate_results
            └── marker_genes
                └── <SAMPLE_NAME>
                    ├── prodigal_translation_table.tsv
                    ├── <SAMPLE_NAME>_pfam_tophit.tsv
                    ├── <SAMPLE_NAME>_pfam.tsv
                    ├── <SAMPLE_NAME>_protein.{faa,fna,gff}
                    ├── <SAMPLE_NAME>_tigrfam.out
                    ├── <SAMPLE_NAME>_tigrfam_tophit.tsv
                    └── <SAMPLE_NAME>_tigrfam.tsv

```



### Results

#### GTDB-Tk

Below is a description of the _per-sample_ results from [GTDB-Tk](https://github.com/Ecogenomics/GTDBTk).
For full details about each of the GTDB output files, see
[GTDB-Tk Classify Workflow](https://github.com/Ecogenomics/GTDBTk#classify-workflow) page.


| Filename | Description |
|-----------|-------------|
| gtdb.(ar122\|bac120).classify.tree | Reference tree in Newick format containing query genomes placed with pplacer |
| gtdb.(ar122\|bac120).filtered.tsv | List of genomes with an insufficient number of amino acids in MSA |
| gtdb.(ar122\|bac120).markers_summary.tsv | Markers used in generation of the concatenated MSA and the order in which they were applied |
| gtdb.(ar122\|bac120).msa.fasta | FASTA file containing MSA of submitted and reference genomes |
| gtdb.(ar122\|bac120).summary.tsv | A summary of classifications provided by GTDB-Tk, see [classification summary](https://github.com/Ecogenomics/GTDBTk#classification-summary-file) for more details |
| gtdb.(ar122\|bac120).user_msa.fasta | FASTA file containing MSA of the submitted genomes |
| gtdb.translation_table_summary.tsv | Summary of the tranlastlation table used for each genome |
| gtdb.(ar122\|bac120).classification_pplacer.tsv | Classification of query genomes based only on their placement in the reference tree |
| gtdb.(ar122\|bac120).red_dictionary.tsv | Median RED values for taxonomic ranks |
| pplacer.(ar122\|bac120).json | Output information generated by pplacer in JSON format |
| pplacer.(ar122\|bac120).out | Output information generated by pplacer |
| gtdb.ar122.markers_summary.tsv | Summary of unique, duplicated, and missing markers within the 122 archaeal marker set for each submitted genome |
| gtdb.bac120.markers_summary.tsv | Summary of unique, duplicated, and missing markers within the 120 bacterial marker set for each submitted genome |
| gtdb.translation_table_summary.tsv | The predicted translation table used for gene calling for each genome |
| marker_genes/ | Contains individual genome results for gene calling using Prodigal and gene identification based on TIGRFAM and Pfam HMMs |





### Audit Trail

Below are files that can assist you in understanding which parameters and program versions were used.

#### Logs 

Each process that is executed will have a `logs` folder containing helpful files for you to review
if the need ever arises.

| Filename                      | Description |
|-------------------------------|-------------|
| nf-&lt;PROCESS_NAME&gt;.begin | An empty file used to designate the process started |
| nf-&lt;PROCESS_NAME&gt;.err   | Contains STDERR outputs from the process |
| nf-&lt;PROCESS_NAME&gt;.log   | Contains both STDERR and STDOUT outputs from the process |
| nf-&lt;PROCESS_NAME&gt;.out   | Contains STDOUT outputs from the process |
| nf-&lt;PROCESS_NAME&gt;.run   | The script Nextflow uses to stage/unstage files and queue processes based on given profile |
| nf-&lt;PROCESS_NAME&gt;.sh    | The script executed by bash for the process  |
| nf-&lt;PROCESS_NAME&gt;.trace | The Nextflow [Trace](https://www.nextflow.io/docs/latest/tracing.html#trace-report) report for the process |
| versions.yml                  | A YAML formatted file with program versions |

#### Nextflow Reports

These Nextflow reports provide great a great summary of your run. These can be used to optimize
resource usage and estimate expected costs if using cloud platforms.

| Filename | Description |
|----------|-------------|
| gtdb-dag.dot | The Nextflow [DAG visualisation](https://www.nextflow.io/docs/latest/tracing.html#dag-visualisation) |
| gtdb-report.html | The Nextflow [Execution Report](https://www.nextflow.io/docs/latest/tracing.html#execution-report) |
| gtdb-timeline.html | The Nextflow [Timeline Report](https://www.nextflow.io/docs/latest/tracing.html#timeline-report) |
| gtdb-trace.txt | The Nextflow [Trace](https://www.nextflow.io/docs/latest/tracing.html#trace-report) report |


#### Program Versions

At the end of each run, each of the `versions.yml` files are merged into the files below.

| Filename                  | Description |
|---------------------------|-------------|
| software_versions.yml     | A complete list of programs and versions used by each process | 
| software_versions_mqc.yml | A complete list of programs and versions formatted for [MultiQC](https://multiqc.info/) |

## Parameters


### Required Parameters
Define where the pipeline should find input data and save output data.

| Parameter | Description | Default |
|---|---|---|
| `--bactopia` | The path to bactopia results to use as inputs |  |

### Filtering Parameters
Use these parameters to specify which samples to include or exclude.

| Parameter | Description | Default |
|---|---|---|
| `--include` | A text file containing sample names (one per line) to include from the analysis |  |
| `--exclude` | A text file containing sample names (one per line) to exclude from the analysis |  |


### GTDB Setup Parameters


| Parameter | Description | Default |
|---|---|---|
| `--gtdb` | Location of a GTDB database. If a database is not found, you must use '--download_gtdb' |  |
| `--download_gtdb` | Download the latest GTDB database, even it exists | False |
| `--skip_check` | Do not check the installation of GTDB database | False |

### GTDB Classify Parameters


| Parameter | Description | Default |
|---|---|---|
| `--min_af` | Minimum alignment fraction to consider closest genome | 0.65 |
| `--min_perc_aa` | Filter genomes with an insufficient percentage of AA in the MSA | 10 |
| `--gtdb_tmp` | Specify alternative directory for temporary files | /tmp |
| `--gtdb_use_scratch` | Reduce pplacer memory usage by writing to --gtdb_tmp location (slower) | False |
| `--gtdb_debug` | Create intermediate files for debugging purposes | False |
| `--force_gtdb` | Continue processing if an error occurs on a single genome | False |


### Optional Parameters
These optional parameters can be useful in certain settings.

| Parameter | Description | Default |
|---|---|---|
| `--outdir` | Base directory to write results to | ./ |
| `--run_name` | Name of the directory to hold results | bactopia |
| `--skip_compression` | Ouput files will not be compressed | False |
| `--keep_all_files` | Keeps all analysis files created | False |

### Max Job Request Parameters
Set the top limit for requested resources for any single job.

| Parameter | Description | Default |
|---|---|---|
| `--max_retry` | Maximum times to retry a process before allowing it to fail. | 3 |
| `--max_cpus` | Maximum number of CPUs that can be requested for any single job. | 4 |
| `--max_memory` | Maximum amount of memory (in GB) that can be requested for any single job. | 32 |
| `--max_time` | Maximum amount of time (in minutes) that can be requested for any single job. | 120 |
| `--max_downloads` | Maximum number of samples to download at a time | 3 |

### Nextflow Configuration Parameters
Parameters to fine-tune your Nextflow setup.

| Parameter | Description | Default |
|---|---|---|
| `--nfconfig` | A Nextflow compatible config file for custom profiles, loaded last and will overwrite existing variables if set. |  |
| `--publish_dir_mode` | Method used to save pipeline results to output directory. | copy |
| `--infodir` | Directory to keep pipeline Nextflow logs and reports. | ${params.outdir}/pipeline_info |
| `--force` | Nextflow will overwrite existing output files. | False |
| `--cleanup_workdir` | After Bactopia is successfully executed, the `work` directory will be deleted. | False |

### Nextflow Profile Parameters
Parameters to fine-tune your Nextflow setup.

| Parameter | Description | Default |
|---|---|---|
| `--condadir` | Directory to Nextflow should use for Conda environments |  |
| `--registry` | Docker registry to pull containers from. | dockerhub |
| `--singularity_cache` | Directory where remote Singularity images are stored. |  |
| `--singularity_pull_docker_container` | Instead of directly downloading Singularity images for use with Singularity, force the workflow to pull and convert Docker containers instead. |  |
| `--force_rebuild` | Force overwrite of existing pre-built environments. | False |
| `--queue` | Comma-separated name of the queue(s) to be used by a job scheduler (e.g. AWS Batch or SLURM) | general,high-memory |
| `--cluster_opts` | Additional options to pass to the executor. (e.g. SLURM: '--account=my_acct_name' |  |
| `--disable_scratch` | All intermediate files created on worker nodes of will be transferred to the head node. | False |

### Helpful Parameters
Uncommonly used parameters that might be useful.

| Parameter | Description | Default |
|---|---|---|
| `--monochrome_logs` | Do not use coloured log outputs. |  |
| `--nfdir` | Print directory Nextflow has pulled Bactopia to |  |
| `--sleep_time` | The amount of time (seconds) Nextflow will wait after setting up datasets before execution. | 5 |
| `--validate_params` | Boolean whether to validate parameters against the schema at runtime | True |
| `--help` | Display help text. |  |
| `--wf` | Specify which workflow or Bactopia Tool to execute | bactopia |
| `--list_wfs` | List the available workflows and Bactopia Tools to use with '--wf' |  |
| `--show_hidden_params` | Show all params when using `--help` |  |
| `--help_all` | An alias for --help --show_hidden_params |  |
| `--version` | Display version text. |  |

## Citations
If you use Bactopia and `gtdb` in your analysis, please cite the following.

- [Bactopia](https://bactopia.github.io/)  
    Petit III RA, Read TD [Bactopia - a flexible pipeline for complete analysis of bacterial genomes.](https://doi.org/10.1128/mSystems.00190-20) _mSystems_ 5 (2020)
  

- [Genome Taxonomy Database](https://gtdb.ecogenomic.org/)  
    Parks DH, Chuvochina M, Rinke C, Mussig AJ, Chaumeil P-A, Hugenholtz P [GTDB: an ongoing census of bacterial and archaeal diversity through a phylogenetically consistent, rank normalized and complete genome-based taxonomy](https://doi.org/10.1093/nar/gkab776) _Nucleic Acids Research_ gkab776 (2021)
  
- [GTDB-Tk](https://github.com/Ecogenomics/GTDBTk)  
    Chaumeil PA, Mussig AJ, Hugenholtz P, Parks DH [GTDB-Tk: a toolkit to classify genomes with the Genome Taxonomy Database.](https://doi.org/10.1093/bioinformatics/btz848) _Bioinformatics_ (2019)
  