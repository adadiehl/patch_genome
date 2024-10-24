# patch_genome.py
## Assemble contigs into a chromosome-scalse pseudo-assembly using alignments to a reference sequence.

Starting with alignments of contigs to a reference genome, produce a chromosome-scale pseudoassembly by patching gaps between mapped contigs with sequences from the reference.

## Dependencies
* Python >= v3.7
* samtools (https://github.com/samtools/samtools)
* pysam (https://github.com/pysam-developers/pysam)

We recommend using minimap2 for alignment, using the -a option to generate SAM output.

## Installation

We recommend installing with conda, into a new environment:
```
conda create -n patch_genome -c conda-forge -c bioconda Bio pysam minimap2 samtools patch_genome
```

Install with pip:
```
pip install patch_genome
```

Installation from the github repository is not recommended. However, if you must, follow the steps below:
1) git clone https://github.com/adadiehl/patch_genome
2) cd patch_genome/
3) python3 -m pip install -e .


## Usage
```
usage: patch_genome.py [-h] -q SAM/BAM -r FASTA [-x BED] [-b FILENAME] [-m N]
                       [-d N] [-f FLOAT] [-e FLOAT]
```

Starting with alignments of contigs to a reference genome, produce a chromosome-scale pseudoassembly by patching gaps between mapped contigs with sequences from the reference. Reference chromosomes with no mapped contigs are printed to output unchanged.

#### Required Arguments
| Argument | Description |
|---|---|
| __-q SAM/BAM, --query_bam SAM/BAM__ | Path to SAM/BAM file containing non-overlapping contig mappings to the reference genome. |
| __-r FASTA, --reference_fasta FASTA__ | Path to reference genome fasta. |

#### Optional Arguments:
| Argument | Description |
|---|---|
| __-h, --help__ | Show this help message and exit. |
| __-x STR, --prefix STR__ | Prefix to add to output file names. Default=None |
| __-b FILENAME, --store_final_bam FILENAME__ | Store the final set of primary contig alignments to the given file name. Default: Do not store the final BAM. |
| __-m N, --min_qual_score N__ | Minimum mapping quality score to retain an alignment. Default=30 |


## Output

patch_genome.py produces three output files:
| File | Description |
|---|---|
| __patched.fasta__ | The final patched genome. |
| __contigs.bed__ | Location of contigs in the coordinate frame of the patched genome. |
| __patches.bed__ | Location of patches in the coordinate frame of the reference genome. |


## Citing patch_genome.py
Please use the following citation if you use this software in your work:

CITATION_HERE