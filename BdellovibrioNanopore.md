## Bdellovibrio Genome Sequencing

### Description

* Target genome: Bdellovibrio bacteriovorus mother strain (109J WT:JWT), mutant strain(109J KNR)
* Sequencing method: Naonopore
* Reference genome: *Bdellovibrio bacteriovorus* strain 109J (NCBI accession: NZ_CP007656)

### Genome Assembly

* Basecalling
  * Basecalling was done by *Guppy basecaller*, GPU mode, **Super accurate model**
  * Configuration file used was dna_r9.4.1_450bps_sup.cfg

* Genome assembly
  * Genome assembly was done by *Flye* assembler
  * Adapter trimming and quality control was done by *PoreChop* and *NanoFilt*, respectively
  * High quality reads were filtered for assembly
  * Threshold were Q-score over 13.5 for WT strain, over 13.75 for KnR strain reads

* Gene annotation
  * Gene annotation was done by *Prodigal*
  * Functional annotation were done by comparining genes to reference genome's annotation
  * *BLASTP* was performed between reference and WT/KnR proteins, WT/KnR proteins with over 99% percent identitiy to reference genes were annotated with reference gene's function

Feature | Reference | WT | KnR
---- | ---- | ---- | ----
Total assembly length | 3,830,427 | 3,836,685 | 3,836,591
Number of contigs | 1 | 1 | 1
GC ratio | 50.65% | 50.65% | 50.65%
Number of genes | 3,647 | 3,727 | 3,766
Genome completeness (*BUSCO*) | 96.0% | 95.2% | 92.7%

### Variant calling

* Variant calling
  * Variant calling was done by *MUMmer*
  * nucmer script was run between reference genome and WT/KnR and between WT and KnR strain
  * Variant information was reported from nucmer result by show-snps script
  * show-snps result was converted to vcf extension file
  * VCF file can be opened by *IGV* genome browser
