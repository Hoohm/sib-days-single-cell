Installation instructions
-------------------------------------

Those are the installation instructions for the single cell workshop at the SIB-Days 2018


### Step 1: Download and install miniconda3
First you need to download and install miniconda3:

for linux
```
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```

for mac os
```
curl https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh -o Miniconda3-latest-MacOSX-x86_64.sh
bash Miniconda3-latest-MacOSX-x86_64.sh
```

### Step 2: Install snakemake and Git

Git is going to be used to get the pipeline and snakemake is the pipeline software

```
conda install git
conda install -c bioconda -c conda-forge snakemake
```

### Step 3: Clone the workflow

Clone the worflow locally. The `--recursive-submodules` will also download the submodule holding some sample data.
```
git clone https://github.com/Hoohm/dropSeqPipe
```

### Step 4: Clone the sample data

```
cd dropSeqPipe
git clone https://github.com/Hoohm/sib-days-single-cell.git
```


Hands on instructions (following the flow of the pre-processing presentation)
-------------------------------------------------

### Step 1: Sequencing quality

This will produce two html reports. One with cell and UMI quality (R1) and one with mRNA (R2) quality.

```
snakemake --use-conda --cores 2 --directory sib-days-single-cell qc
```

### Step 2: Filtering

This will produce a trimmomatic report as well as a few plots linked to filtering

```
snakemake --use-conda --cores 2 --directory sib-days-single-cell filter
```

### Step 3: Mapping

This will produce a STAR html report as well as the yield plot

```
snakemake --use-conda --cores 2 --directory sib-days-single-cell map
```

### Step 4: Demultiplexing and extracting

This will produce the final umi_expression_matrix.tsv in the summary folder
```
snakemake --use-conda --cores 2 --directory sib-days-single-cell extract
```
