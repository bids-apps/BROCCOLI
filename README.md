## Description

BROCCOLI is a software for analysis of fMRI (functional magnetic resonance imaging) data and is written in OpenCL (Open Computing Language). The analysis can thereby be performed in parallel on many types of hardware, such as CPUs, Nvidia GPUs and AMD GPUs. The result is a significantly faster analysis than possible with other software packages for fMRI analysis. For example, non-linear normalization of an anatomical T1 volume to MNI space (1mm resolution) takes only 4-8 seconds with a GPU.

## Documentation

Please read the official [BROCCOLI](https://github.com/wanderine/BROCCOLI/raw/master/documentation/broccoli.pdf) documentation

##Error reporting

Experiencing problems? Please open an [issue](https://github.com/wanderine/BROCCOLI/issues/new)

## Acknowledgement

When using this pipeline, please acknowledge us by citing

[Eklund, A., Dufort, P., Villani, M., LaConte, S., BROCCOLI: Software for Fast fMRI Analysis on Many-Core CPUs and GPUs, Frontiers in Neuroinformatics, 8:24, 2014](http://journal.frontiersin.org/Journal/10.3389/fninf.2014.00024/abstract)

## Usage

Command-line usage of the processing script [broccolipipeline.sh](https://github.com/wanderine/BROCCOLI/blob/master/code/bids/broccolipipeline.sh) is as follows:

#### Synopsis

    ./broccolipipeline.sh bids_dir output_dir analysis_level

-  *bids_dir*: The directory with the input dataset formatted according to the BIDS standard.
-  *output_dir*: The directory where the output files should be stored. If you are running group level analysis, this folder should be prepopulated with the results of the participant level analysis.
-  *analysis_level*: Level of the analysis that will be performed. Multiple participant level analyses can be run independently (in parallel) using the same output_dir. Options are: participant and group.

## Options

#### Options specific to the batch processing of subject data

+ **--participant_label**<br>The label(s) of the participant(s) that should be analyzed. The label(s) correspond(s) to sub-<participant_label> from the BIDS spec (so it does _not_ include "sub-"). If this parameter is not provided, all subjects will be analyzed sequentially. Multiple participants can be specified with a space-separated list.



##Instructions

The bids/broccoli Docker container enables users to run fMRI analyses in parallel using OpenCL. The pipeline requires that data be organized in accordance with the BIDS specification.

To get a Docker container with BROCCOLI pre-installed, run

```{bash}
$ docker pull bids/broccoli:v1.0.0
```

To run a first level analysis of all subjects in a BIDS dataset, run

```{bash}
$ docker run -i --rm \
    -v /Users/yourname/data/ds005:/bids_dataset \
    -v /Users/yourname/outputs:/outputs \
    bids/broccoli:v1.0.0 \
    /bids_dataset /outputs participant
```

To run a first level analysis of subject 01 only, run

```{bash}
$ docker run -i --rm \
    -v /Users/yourname/data/ds005:/bids_dataset \
    -v /Users/yourname/outputs:/outputs \
    bids/broccoli:v1.0.0 \
    /bids_dataset /outputs participant --participant_label 01
```

To run a group analysis of all subjects, run

```{bash}
$ docker run -i --rm \
    -v /Users/yourname/data/ds005:/bids_dataset \
    -v /Users/yourname/outputs:/outputs \
    bids/broccoli:v1.0.0 \
    /bids_dataset /outputs group
```


### Commercial use

This BIDS App is using [FSL](https://fsl.fmrib.ox.ac.uk/). If you are considering commercial use of this App please consult the relevant licenses.
