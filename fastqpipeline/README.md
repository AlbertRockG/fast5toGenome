
# Fastqpipeline : Bacterial Isolate Genome Sequencing Data Processing pipeline

fastqpipeline is designed to process bacterial isolate whole genome sequencing data obtained using Nanopore sequencing technology (ONT). The pipeline takes single fastq.gz file per sample as input and includes both assembling with flye and polishing with medaka of the genome sequences. This pipeline has been design and tested on ubuntu 22.04. You may face some issues while trying to run it in other linux distributions.

```
OPTIONS:

-i: Path to input directory containing compressed fastq files (Example: sample_name.fastq.gz).
-o: Path to the directory where processed data will be stored. This directory will be created if it doesn't exist.
-m: Medaka model for consensus polishing.
-t: Number of threads to provide for the analysis (optional).
-b: GPU memory control for medaka (optional).
-v: Enable verbosity (optional).
```

## Instructions to running fastqpipeline 
### Setup environment
Before using this pipeline, you need to setup the required environment by installing the following software, if they are not already installed:
- [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) 
- [mamba](https://mamba.readthedocs.io/en/latest/mamba-installation.html#mamba-install) in conda base environment
- Create the environment named `medaka`
- [flye 2.9.2-b1786 or above](https://github.com/fenderglass/Flye) (To be installed with conda)
- [medaka 1.8.0 or above](https://anaconda.org/bioconda/medaka) (To be installed with conda)

### Run fastqpipeline

To run this pipeline, kindly follow this instructions in your terminal from your home directory:

```bash
# To get the pipeline source code on your laptop
git clone https://github.com/AlbertRockG/fast5toGenome

# To add fastqpipeline to the PATH if using bash shell
echo "export PATH=$PATH:$HOME/fast5Genome" >> .bashrc
source .bashrc

# To activate the medaka environment, if using conda
conda activate medaka

# Example of running
fastqpipeline -i data/IN_DIR \\
                -o data/OUT_DIR \\
                -m r941_min_hac_g507 \\
                -v
```

## Acknowledgments

I would like to express my gratitude to the following individuals and organizations for their valuable contributions and support:

- [Marco](https://github.com/zwets), a senior Bioinformatician, for providing guidance and assistance throughout the process.
- FAO (Food and Agriculture Organization), SeqAfrica, and FlemingFund for their support in funding and resources.
- The Noguchi Memorial Institute for Medical Research for providing the infrastructure and facilities for this project.

## License

MIT License

Copyright (c) 2023 Albert Rock A. Gangbadja

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
