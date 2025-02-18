**Euprymna scolopes gene annotation for V2 genome**  

This repo contains the gene annotation (new BRAKER2 models, combined with some genes from Belcaid *et al*. 2019) for the Hawaiian bobtail squid, *Euprymna scolopes* genome (Schmidbaur *et al.*, 2022). It is published in the following manuscript: Rogers, T.F., Yalçın, G., Briseno, J., Vijayan, N., Nyholm, S. V. & Simakov, O.  Gene modelling and annotation for the Hawaiian bobtail squid, *Euprymna scolopes*. *Sci Data* 11, 40 (2024). https://doi.org/10.1038/s41597-023-02903-8

The corresponding genome assembly can be found here: https://metazoa.csb.univie.ac.at/data/v2/ or on NCBI here: https://www.ncbi.nlm.nih.gov/datasets/genome/GCA_024364805.1/

**The annotation files are as follows:**  
  
eupsc_models_v2.2.gtf #Gene annotation GTF  
eupsc_models_v2.2_cds.fa #Coding sequence file  
eupsc_models_v2.2_prot.fa #Protein sequence file  
eupsc_models_v2.2_interproscan.tsv #Protein annotation  
eupsc_models_v2.2.tags.gtf #Same gene annotation gtf as eupsc_models_v2.2.gtf but with explicit exon lines
eupsc_models_v2.2.tags.ncbi.gtf #Same as eupsc_models_v2.2.tags.gtf but with chromosome/scaffold names that match the genome assembly on NCBI

Information on column headers for eupsc_models_v2.2.gtf and eupsc_models_v2.2.tags.gtf can be found here: <https://www.ensembl.org/info/website/upload/gff.html>

Information on column headers for eupsc_models_v2.2_interproscan.tsv can be found here: <https://interproscan-docs.readthedocs.io/en/latest/OutputFormats.html>
  
**List of commands used to generate the annotation can be found in these files:**  
1. Iso-Seq processing and mapping  
2. Run BRAKER2, format output and run BUSCO  
3. Add Belcaid models missed in BRAKER, run BUSCO and Interproscan, count orthologs and format gtf
  
TSEBRA was also run to select the best genes from Iso-Seq data and BRAKER2 models as suggested by reviewer 2. However, this decreased BUSCO completeness scores so was not used as the final annotation. **The gtf output from TSEBRA and commands run (for reviewers only) can be found here**:  

tsebra_withGushr_longread.gtf #Do not use as gene annotation file, has less complete BUSCO scores than the gtfs above  
4. TSEBRA  
  
**Scripts used are as follows:** 
  
braker2_eupsc_isoseq_rnaseq_prot.sh #BRAKER2 SLURM script 1 for making gene models with RNA-seq, Iso-Seq from  E. scolopes and protein files from other species  
braker2_eupsc_isoseq_rnaseq_utron.sh #BRAKER2 SLURM script 2 for adding UTRs to the output of the first BRAKER2 script above  
convertBraker2Gff.pl #Script for formatting BRAKER2 output gtf  
obtainBelcaidGeneList3.pl #Script for creating non-overlapping (more than 75% of exons unique) and multi-exon Belcaid et al. (2019) genes  
countExonPerGene.pl #Count number of multi- and single-exon genes that are annotated and unannotated in Interproscan  





