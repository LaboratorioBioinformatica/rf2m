# Mutant Genome Creator

**Mutant Genome Creator** is a software developed to modify genomes based on VCF files with SNPs and indels present in cell lines or strains. The software also create a new annotation file (GTF) for the mutant genome with updated coordinates of the genes.

## Requirements

To run **Mutant Genome Creator** you only need to have Perl (I think any versions works, but my Perl version is 5.26.1) installed on your machine. The software also does not need to be installed.

## VCF file format

The specifications for VCF format are described [here](https://samtools.github.io/hts-specs/VCFv4.2.pdf). The script does not work for structural variants, only for SNPs and small indels. In the present version of **Mutant Genome Creator** only the SNPs and indels with **PASS** in the FILTER field will be processed. We are studying to include an option where the user can choose the Filter value in next versions. The script also does not process the lines in VCF with more than one alternative allele in ALT field. Below has an example: The first line will be processed, and the second will not be processed.

|CHROM | POS | ID | REF | ALT | QUAL | FILTER | INFO |
|------|-----|----|-----|-----|------|--------|------|
|20    |2    |.   |TC   |TCA  |.     |PASS    |DP=100|
|20    |2    |.   |TC   |TG,T |.     |PASS    |DP=100|

## Running

Run the command lines below in the folder where you downloaded **Mutant Genome Creator** script:

`chmod +x mutant_genome_creator`

`./mutant_genome_creator --vcf input.vcf --genome input_genome.fasta --gtf input.gtf --outGenome output_genome.fasta --outGTF output.gtf`

### Options
|Option      |Description                                                                       |
|------------|----------------------------------------------------------------------------------|
|--vcf       |File with SNPs and indels in VCF format                                           |
|--genome    |File with reference genome in FASTA format                                        |
|--gtf       |File with annotation for reference genome in GTF format                           |
|--outGenome |Name for the output file of the modified genome in FASTA format                   |
|--outGTF    |Name for the output file of the annotation for the modified genome in GTF format  |
