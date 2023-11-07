
# Fast5pipeline : Bacterial Isolate Genome Sequencing Data Processing pipeline

fast5pipeline is designed to process bacterial isolate whole genome sequencing data obtained using Nanopore sequencing technology (ONT). The pipeline takes fast5 files as input and includes basecalling, demultiplexing, assembling, and polishing of the genome sequences. This pipeline has been design and tested on ubuntu 22.04. You may face some issues while trying to run it in other linux distributions.

```
OPTIONS:

-c: Path to the Guppy configuration file.
-i: Path to the directory containing the raw nanopore sequencing data (fast5 files)
-o: Path to the directory where processed data will be stored. This directory will be created if it doesn't exist.
-k: Barcode kits to be used for barcoding.
-m: medaka model for consensus polishing.
-b: GPU memory control for medaka (optional)
-v: Enable verbosity.
```

## Instructions to running fast5pipeline 
### Setup environment
Before using this pipeline, you need to setup the required environment by installing the following software, if they are not already installed:

- [Guppy Basecalling Software](https://community.nanoporetech.com/docs/prepare/library_prep_protocols/Guppy-protocol/v/gpb_2003_v1_revax_14dec2018/linux-guppy), (C) Oxford Nanopore Technologies plc. Version 6.5.7+ca6d6af, minimap2 version 2.24-r1122 or above
- [GNU gzip](https://www.gnu.org/software/gzip/)
- [flye 2.9.2-b1786](https://github.com/fenderglass/Flye) or above
- [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) or [mamba](https://mamba.readthedocs.io/en/latest/mamba-installation.html#mamba-install)
- [medaka 1.8.0 or above](https://anaconda.org/bioconda/medaka) (To be installed with conda or mamba in an environment named medaka)

### Run fast5pipeline

To run this pipeline, kindly follow this instructions:

```bash
git clone https://github.com/AlbertRockG/fast5toGenome
cd fast5Genome/
export PATH="$PWD/fast5Genome:$PATH"
# To activate the medaka environment, if using conda
conda activate medaka

# Example of running
./fast5pipeline -c dna_r9.4.1_450bps_hac.cfg \\
                -i data/IN_DIR \\
                -o data/OUT_DIR \\
                -k SQK-RBK110-96 \\
                -m r941_min_hac_g507 \\
                -v
```

## Acknowledgments

I would like to express my gratitude to the following individuals and organizations for their valuable contributions and support:

- [Marco](https://github.com/zwets), a senior Bioinformatician, for providing guidance and assistance throughout the process.
- FAO (Food and Agriculture Organization), SeqAfrica, and FlemingFund for their support in funding and resources.
- The Noguchi Memorial Institute for Medical Research for providing the infrastructure and facilities for this project.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
