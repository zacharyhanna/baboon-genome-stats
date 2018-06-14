# baboon-genome-stats

## Tool set-up  

### BUSCO  
We ran BUSCO version 3.0.2 with the Euarchontoglires ortholog set version 2017-02-13.  

### assemblathon-stats-ex.pl  
We obtained assemblathon-stats-ex.pl from NSO-genome-scripts version 1.0.0 (Bradnam et al., 2013; Hanna & Henderson, 2017).  

## assembly-stats  
We obtained assembly-stats commit f5a9e95f4d6f8c2cb19fae529db9b6215ef5c954 (Hunt, 2018).  
```
git clone https://github.com/sanger-pathogens/assembly-stats.git  
mkdir build  
cd build  
cmake -DINSTALL_DIR:PATH=/media/walllab/zhanna/bin/assembly-stats-made ..  
make  
make test  
make install  
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
Bradnam KR., Fass JN., Alexandrov A., Baranay P., Bechner M., Birol I., Boisvert S., Chapman JA., Chapuis G., Chikhi R., Chitsaz H., Chou W-C., Corbeil J., Del Fabbro C., Docking TR., Durbin R., Earl D., Emrich S., Fedotov P., Fonseca NA., Ganapathy G., Gibbs RA., Gnerre S., Godzaridis E., Goldstein S., Haimel M., Hall G., Haussler D., Hiatt JB., Ho IY., Howard J., Hunt M., Jackman SD., Jaffe DB., Jarvis ED., Jiang H., Kazakov S., Kersey PJ., Kitzman JO., Knight JR., Koren S., Lam T-W., Lavenier D., Laviolette F., Li Y., Li Z., Liu B., Liu Y., Luo R., MacCallum I., MacManes MD., Maillet N., Melnikov S., Naquin D., Ning Z., Otto TD., Paten B., Paulo OS., Phillippy AM., Pina-Martins F., Place M., Przybylski D., Qin X., Qu C., Ribeiro FJ., Richards S., Rokhsar DS., Ruby JG., Scalabrin S., Schatz MC., Schwartz DC., Sergushichev A., Sharpe T., Shaw TI., Shendure J., Shi Y., Simpson JT., Song H., Tsarev F., Vezzi F., Vicedomini R., Vieira BM., Wang J., Worley KC., Yin S., Yiu S-M., Yuan J., Zhang G., Zhang H., Zhou S., Korf IF. 2013. Assemblathon 2: evaluating de novo methods of genome assembly in three vertebrate species. GigaScience 2:10. DOI: 10.1186/2047-217X-2-10.  

Hanna ZR, Henderson JB. 2017. NSO-genome-scripts Version 1.0.0. Zenodo. DOI: 10.5281/zenodo.805012  

Hunt M. 2018. assembly-stats. [Accessed 2018 June 14]. Available at: https://github.com/sanger-pathogens/assembly-stats  
