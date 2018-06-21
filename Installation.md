This pipeline is dependent on conda.

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
git clone --recurse-submodules https://github.com/Hoohm/dropSeqPipe
```

### Step 4: Create the environments

In snakemake each rule can be given a specific environment that has to be created to run. They are located in the `envs` folder and are referenced by the `conda:` line.

Using snakemake with the `--use-conda` tag will look for those envs, download and create the environments for us.

```
cd dropSeqPipe
snakemake --use-conda --directory .test/ --create-envs-only
```
*Note that you don't have to create them in advance, this is just in order to not have to debug some potential issues on the workshop day*

### Step 5: Generate the metadata and STAR index

Change N according to the number of threads you have available

```
snakemake --use-conda --cores N --directory .test/ meta
```