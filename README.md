# baboon-genome-stats

## Tool set-up  

### BUSCO  
We ran BUSCO version 3.0.2 with the Euarchontoglires ortholog set version 2017-02-13.  

###

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

 to create the assembly without the mapping to human
chromosomes.  
```

```

```
python /media/walllab/zhanna/.linuxbrew/bin/busco -i Panu3_unchrom.fa -o Panu3_busco20180607 -l /media/walllab/zhanna/baboon_genome/euarchontoglires_odb9/ -m genome -c 1 -sp human
```

## References  
