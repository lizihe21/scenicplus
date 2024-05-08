![alt text](docs/images/SCENIC+_Logo_v5.png "SCENIC+")
[![Documentation Status](https://readthedocs.org/projects/scenicplus/badge/?version=latest)](https://scenicplus.readthedocs.io/en/latest/?badge=latest)
[![DOI](https://zenodo.org/badge/391121521.svg)](https://zenodo.org/badge/latestdoi/391121521)
# Old version SCENIC+ suitabe for non model organism

# SCENIC+ single-cell eGRN inference

> [!TIP]
> We did a live webinar on using the SCENIC+ workflow. You can rewatch it on [YouTube](https://www.youtube.com/watch?v=QW63LLd1XC8)


`SCENIC+` is a python package to build gene regulatory networks (GRNs) using combined or separate single-cell gene expression (scRNA-seq) and single-cell chromatin accessibility (scATAC-seq) data.

## Documentation 


Extensive documentation and tutorials are available at [read the docs](https://scenicplus.readthedocs.io).

## Installing

To install SCENIC+ (in a Linux environment):

```bash
pip install -e git+https://github.com/lizihe21/scenicplus@old
```


## Creating a Docker/Singularity Image

To build a Docker image, and then create a Singularity image from this:

```bash
# Clone repositories 
git clone https://github.com/aertslab/pySCENIC.git
git clone https://github.com/aertslab/LoomXpy.git
git clone https://github.com/aertslab/pycisTopic.git
git clone https://github.com/aertslab/pycistarget.git
git clone https://github.com/aertslab/scenicplus.git

# Login
podman login docker.io

# Build image
podman build -t aertslab/scenicplus:latest . -f scenicplus/Dockerfile

# Export to oci 
podman save --format oci-archive --output scenicplus_img.tar localhost/aertslab/scenicplus

# Build to singularity
singularity build scenicplus.sif oci-archive://scenicplus_img.tar

# Add all binding paths where you would need to access
singularity exec -B /lustre1,/staging,/data,/vsc-hard-mounts,/scratch scenicplus.sif ipython3
```

## Check version

To check your SCENIC+ version:

```bash
import scenicplus
scenicplus.__version__
```

## Questions?

* If you have **technical questions or problems**, such as bug reports or ideas for new features, please open an issue under the issues tab.
* If you have **questions about the interpretation of results or your analysis**, please start a Discussion under the Discussions tab.


## References

[Bravo Gonzalez-Blas, C. & De Winter, S. *et al.* (2022). SCENIC+: single-cell multiomic inference of enhancers and gene regulatory networks](https://www.biorxiv.org/content/10.1101/2022.08.19.504505v1)

