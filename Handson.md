Pre-processing the data
-------------------------------------

Those are the instructions for the *hands on* single cell workshop at the SIB-Days 2018


### Step 1: Sequencing quality control

```
snakemake --use-conda --cores 2 --directory .test/ qc
```


### Step 2: Filtering

```
snakemake --use-conda --cores 2 --directory .test/ filter
```

### Step 3: Mapping

```
snakemake --use-conda --cores 2 --directory .test/ map
```

### Step 4: Demultiplexing and extracting

```
snakemake --use-conda --cores 2 --directory .test/ extract
```