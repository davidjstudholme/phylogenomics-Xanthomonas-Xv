# phylogenomics-Xanthomonas-Xv

```
### Download NCBI Datasets command line tools
curl -o datasets 'https://ftp.ncbi.nlm.nih.gov/pub/datasets/command-line/v1/linux-amd64/datasets'
chmod u+x datasets 

### Create genomes directory and download genome assemblies 
mkdir genomes
cd genomes

ln -s ../Xv_assemblies_acc_06_06_23.txt .
ln -s ../datasets .
./datasets download genome accession --inputfile Xv_assemblies_acc_06_06_23.txt  --exclude-gff3 --exclude-protein --exclude-rna --exclude-genomic-cds --filename xanthomonas_genome_assemblies.zip

unzip xanthomonas_genome_assemblies.zip
ln -s ncbi_dataset/data/GCA_*/GCA_*.fna .

unzip xanthomonas_genome_assemblies.zip
ls *.fna
perl rename_files.pl  genomes.txt

cd -


### Set-up the ref/ directory
mkdir ref
cd ref
ln -s ../genomes/NCPPB_4379.fasta

cd -


### Set-up the workdir/ directory
mkdir workdir
cd workdir
ln -s ../genomes/*.contig .
cd -

### Run PhaME
### Shakya, M., Ahmed, S.A., Davenport, K.W. et al. 
### Standardized phylogenetic and molecular evolutionary analysis applied to species across the microbial tree of life. 
### Sci Rep 10, 1723 (2020). 
### https://doi.org/10.1038/s41598-020-58356-1

screen
conda activate phame
cp phylogenomics-Xanthomonas-1/phame.ctl .
./phame ./phame.ctl



```
