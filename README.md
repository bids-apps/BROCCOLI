##Description

BROCCOLI is a software for analysis of fMRI (functional magnetic resonance imaging) data and is written in OpenCL (Open Computing Language). The analysis can thereby be performed in parallel on many types of hardware, such as CPUs, Nvidia GPUs and AMD GPUs. The result is a significantly faster analysis than possible with other software packages for fMRI analysis. For example, non-linear normalization of an anatomical T1 volume to MNI space (1mm resolution) takes only 4-8 seconds with a GPU.

##Documentation

Please read the official [BROCCOLI](https://github.com/wanderine/BROCCOLI/raw/master/documentation/broccoli.pdf) documentation

##Error reporting

Experiencing problems? Please open an [issue](https://github.com/wanderine/BROCCOLI/issues/new)

##Acknowledgement

When using this pipeline, please acknowledge us by citing

[Eklund, A., Dufort, P., Villani, M., LaConte, S., BROCCOLI: Software for Fast fMRI Analysis on Many-Core CPUs and GPUs, Frontiers in Neuroinformatics, 8:24, 2014](http://journal.frontiersin.org/Journal/10.3389/fninf.2014.00024/abstract)

##Instructions

The bids/broccoli Docker container enables users to run fMRI analyses in parallel using OpenCL. The pipeline requires that data be organized in accordance with the BIDS spec. If the data you wish to process is available on S3 you simply need to provide your s3 credentials at build time and the pipeline will auto-retrieve your data for processing.

To get your container ready to run just follow these steps:

(A) I do not wish to use S3:

In your terminal, type:

```{bash}
$ docker pull bids/broccoli
```


### Commercial use

This BIDS App is using [FSL](https://fsl.fmrib.ox.ac.uk/). If you are considering commercial use of this App please consult the relevant licenses.
