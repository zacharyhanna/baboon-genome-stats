# baboon-genome-stats
We here provide details of our assessment of the completeness and continuity of
*Papio anubis* assemblies.  

## Tool set-up  

### BUSCO  
We installed BUSCO version 3.0.2 (Simão et al., 2015; Waterhouse et al., 2018) with the Euarchontoglires ortholog set version 2017-02-13 (Zdobnov et al., 2017). BUSCO utilized NCBI's BLAST+ version 2.7.1 (Camacho et al., 2009), HMMER version 3.1b2 (http://hmmer.org), and AUGUSTUS version 3.3.1 (Keller et al., 2011; Stanke et al., 2018).  

BUSCO requires the user to set parameters in a configuration file "config.ini", a copy of which we have provided in this repository (BUSCO_config.ini).  

### assemblathon-stats-ex.pl  
We obtained assemblathon-stats-ex.pl from NSO-genome-scripts version 1.0.0 (Bradnam et al., 2013; Hanna & Henderson, 2017).  We used this script to calculate a variety of assembly continuity statistics at both the scaffold and contig level.  

## assembly-stats  
We obtained assembly-stats commit f5a9e95f4d6f8c2cb19fae529db9b6215ef5c954 (Hunt, 2018) and followed the installation instructions.  
```
git clone https://github.com/sanger-pathogens/assembly-stats.git  
mkdir build  
cd build  
cmake -DINSTALL_DIR:PATH=/media/walllab/zhanna/bin/assembly-stats-made ..  
make  
make test  
make install  
```
We used this tool to calculate N60-N90 and L60-L90 statistics.  

## 28246_hybrid assembly  
* Assembly file: 28246_hybrid_ALL.fa  

* BUSCO  
```
busco -c 8 -i 28246_hybrid_ALL.fa -l euarchontoglires_odb9 -m genome --blast_single_core -sp human -o 228246_hybrid_busco  
```

* assemblathon-stats-ex.pl  
```
perl assemblathon-stats-ex.pl -csv 28246_hybrid_ALL.fa  
```

* assembly-stats  
```
assembly-stats 28246_hybrid_ALL.fa >28246_hybrid_ALL.fa_assembly-stats  
```

## Panu2.0  
* Obtained Panu2.0 assembly files  
```
wget ftp://ftp.ncbi.nlm.nih.gov/genomes/genbank/vertebrate_mammalian/Papio_anubis/all_assembly_versions/GCA_000264685.1_Panu_2.0/GCA_000264685.1_Panu_2.0_assembly_structure/Primary_Assembly/unplaced_scaffolds/FASTA/unplaced.scaf.fna.gz  
wget ftp://ftp.ncbi.nlm.nih.gov/genomes/genbank/vertebrate_mammalian/Papio_anubis/all_assembly_versions/GCA_000264685.1_Panu_2.0/GCA_000264685.1_Panu_2.0_assembly_structure/Primary_Assembly/placed_scaffolds/FASTA/*.fna.gz  
```

* Combined Panu2.0 assembly files  
```
zcat *.fna.gz >Panu2_unchrom.fa  
```

* BUSCO  
```
busco -c 8 -i Panu2_unchrom.fa -l /media/walllab/zhanna/baboon_genome/euarchontoglires_odb9 -m genome --blast_single_core -sp human -o Panu2_unchrom_busco  
```

* assemblathon-stats-ex.pl  
```
perl assemblathon-stats-ex.pl -csv Panu2_unchrom.fa  
```

* assembly-stats  
```
assembly-stats Panu2_unchrom.fa >Panu2_unchrom.fa_assembly-stats  
```

## Panu3.0  
* Obtained 3.0 assembly files  
```
wget https://ftp.ncbi.nlm.nih.gov/genomes/genbank/vertebrate_mammalian/Papio_anubis/latest_assembly_versions/GCA_000264685.2_Panu_3.0/GCA_000264685.2_Panu_3.0_assembly_structure/Primary_Assembly/placed_scaffolds/FASTA/*.fna.gz  
wget https://ftp.ncbi.nlm.nih.gov/genomes/genbank/vertebrate_mammalian/Papio_anubis/latest_assembly_versions/GCA_000264685.2_Panu_3.0/GCA_000264685.2_Panu_3.0_assembly_structure/Primary_Assembly/unplaced_scaffolds/FASTA/unplaced.scaf.fna.gz  

```
* Combined Panu3.0 assembly files  
```
zcat *.fna.gz >Panu3_unchrom.fa  
```

* BUSCO
```
busco -i Panu3_unchrom.fa -l /media/walllab/zhanna/baboon_genome/euarchontoglires_odb9 -m genome --blast_single_core -sp human -o Panu3_busco  
```

* assemblathon-stats-ex.pl  
```
perl assemblathon-stats-ex.pl -csv Panu3_unchrom.fa  
```

* assembly-stats  
```
assembly-stats Panu3_unchrom.fa >Panu3_unchrom.fa_assembly-stats  
```


## References  
Bradnam KR., Fass JN., Alexandrov A., Baranay P., Bechner M., Birol I., Boisvert S., Chapman JA., Chapuis G., Chikhi R., Chitsaz H., Chou W-C., Corbeil J., Del Fabbro C., Docking TR., Durbin R., Earl D., Emrich S., Fedotov P., Fonseca NA., Ganapathy G., Gibbs RA., Gnerre S., Godzaridis E., Goldstein S., Haimel M., Hall G., Haussler D., Hiatt JB., Ho IY., Howard J., Hunt M., Jackman SD., Jaffe DB., Jarvis ED., Jiang H., Kazakov S., Kersey PJ., Kitzman JO., Knight JR., Koren S., Lam T-W., Lavenier D., Laviolette F., Li Y., Li Z., Liu B., Liu Y., Luo R., MacCallum I., MacManes MD., Maillet N., Melnikov S., Naquin D., Ning Z., Otto TD., Paten B., Paulo OS., Phillippy AM., Pina-Martins F., Place M., Przybylski D., Qin X., Qu C., Ribeiro FJ., Richards S., Rokhsar DS., Ruby JG., Scalabrin S., Schatz MC., Schwartz DC., Sergushichev A., Sharpe T., Shaw TI., Shendure J., Shi Y., Simpson JT., Song H., Tsarev F., Vezzi F., Vicedomini R., Vieira BM., Wang J., Worley KC., Yin S., Yiu S-M., Yuan J., Zhang G., Zhang H., Zhou S., Korf IF. 2013. Assemblathon 2: evaluating de novo methods of genome assembly in three vertebrate species. *GigaScience* 2:10. DOI: 10.1186/2047-217X-2-10.  

Camacho C, Coulouris G, Avagyan V, Ma N, Papadopoulos J, Bealer K, et al. 2009. BLAST+: architecture and applications. *BMC Bioinformatics* 10: 421. DOI: 10.1186/1471-2105-10-421  

Hanna ZR, Henderson JB. 2017. NSO-genome-scripts Version 1.0.0. *Zenodo*. DOI: 10.5281/zenodo.805012  

Hunt M. 2018. assembly-stats. [Accessed 2018 June 14]. Available at: https://github.com/sanger-pathogens/assembly-stats  

Keller O, Kollmar M, Stanke M, Waack S. 2011. A novel hybrid gene prediction method employing protein multiple sequence alignments. *Bioinformatics* 27: 757–763. DOI: 10.1093/bioinformatics/btr010  

Simão FA, Waterhouse RM, Ioannidis P, Kriventseva EV, Zdobnov EM. 2015. BUSCO: assessing genome assembly and annotation completeness with single-copy orthologs. *Bioinformatics* 31: 3210–3212. DOI: 10.1093/bioinformatics/btv351  

Stanke M, Keller O, König S, Gerischer L, Romoth L. 2018. AUGUSTUS. Version 3.3.1. [Accessed 2018 Jun 14]. Available from: http://bioinf.uni-greifswald.de/augustus  

Waterhouse RM, Seppey M, Simão FA, Manni M, Ioannidis P, Klioutchnikov G, et al. 2018. BUSCO Applications from Quality Assessments to Gene Prediction and Phylogenomics. *Mol Biol Evol* 35: 543–548. DOI: 10.1093/molbev/msx319  

Zdobnov EM, Tegenfeldt F, Kuznetsov D, Waterhouse RM, Simão FA, Ioannidis P, et al. 2017. OrthoDB v9.1: cataloging evolutionary and functional annotations for animal, fungal, plant, archaeal, bacterial and viral orthologs. *Nucleic Acids Res* 45: D744–D749. DOI: 10.1093/nar/gkw1119  
