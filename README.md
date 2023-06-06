# phylogenomics-Xanthomonas-Xv

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
ln -s ncbi_dataset/data/GCA_*/GCA_*.fna .
ls *.fna
perl ../phylogenomics-Xanthomonas-1/rename_files.pl  ../phylogenomics-Xanthomonas-1/genomes.txt

cd -

