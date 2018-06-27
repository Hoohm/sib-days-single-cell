Pre-processing the data
-------------------------------------

Those are the instructions for the *hands on* single cell workshop at the SIB-Days 2018

### Step 0: Download the repo

```
git clone https://github.com/Hoohm/sib-days-single-cell.git
```


### Step 1: Sequencing quality control

```
snakemake --use-conda --cores 2 --directory sib-days-single-cell qc
```


### Step 2: Filtering

```
snakemake --use-conda --cores 2 --directory sib-days-single-cell filter
```

### Step 3: Mapping

```
snakemake --use-conda --cores 2 --directory sib-days-single-cell map
```

### Step 4: Demultiplexing and extracting

```
snakemake --use-conda --cores 2 --directory sib-days-single-cell extract
```