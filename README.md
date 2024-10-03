# bioe

安装week4-5用的软件包：
conda install -c bioconda prodigal prokka

week4-5：

q1：
cd /home/zhany0y/fond_of_bioe/week5-github/bioe/
python week5-q1.py

outp：
The number of amino acids in the encoded peptide (not including the stop codon) is 30.
The open reading frame of the DNA sequence encoding the amino acids (including the stop codon) contains 93 bases.

q2：
conda activate bioe
prodigal -i /home/zhany0y/fond_of_bioe/week5-github/bioe/ncbi_dataset/data/GCF_000091085.2/GCF_000091085.2_ASM9108v2_genomic.fna -o genes.gff
grep -c "CDS" genes.gff
outp：1057

q3：
bash week5-q3.sh
outp：
File Name | Annotated Gene Count
test.fna | 897
nucleotides.fna | 895
GCA_000006825.1_ASM682v1_genomic.fna | 2032
GCA_000006865.1_ASM686v1_genomic.fna | 2383
GCA_000007125.1_ASM712v1_genomic.fna | 3152
GCA_000008785.1_ASM878v1_genomic.fna | 1505
GCA_000091085.2_ASM9108v2_genomic.fna | 1063
GCF_000006825.1_ASM682v1_genomic.fna | 2032
GCF_000006865.1_ASM686v1_genomic.fna | 2383
GCF_000007125.1_ASM712v1_genomic.fna | 3152
GCF_000008785.1_ASM878v1_genomic.fna | 1505
GCF_000091085.2_ASM9108v2_genomic.fna | 1057
GCA_000006745.1_ASM674v1_genomic.fna | 3594
GCA_000008545.1_ASM854v1_genomic.fna | 1866
GCA_000008565.1_ASM856v1_genomic.fna | 3248
GCA_000008725.1_ASM872v1_genomic.fna | 897
GCA_000027305.1_ASM2730v1_genomic.fna | 1748
GCF_000006745.1_ASM674v1_genomic.fna | 3594
GCF_000008545.1_ASM854v1_genomic.fna | 1866
GCF_000008565.1_ASM856v1_genomic.fna | 3248
GCF_000008725.1_ASM872v1_genomic.fna | 897
GCF_000027305.1_ASM2730v1_genomic.fna | 1748
GCA_000008525.1_ASM852v1_genomic.fna | 1579
GCA_000008605.1_ASM860v1_genomic.fna | 1009
GCA_000008625.1_ASM862v1_genomic.fna | 1776
GCA_000008745.1_ASM874v1_genomic.fna | 1063
GCF_000008525.1_ASM852v1_genomic.fna | 1579
GCF_000008605.1_ASM860v1_genomic.fna | 1009
GCF_000008625.1_ASM862v1_genomic.fna | 1776
GCF_000008745.1_ASM874v1_genomic.fna | 1063

q4：
bash week5-q4.sh
outp：
./ibex-miniconda-install/test.fna has 908 genes
./ibex-miniconda-install/nucleotides.fna has 847 genes
./ncbi_dataset/data/GCA_000006825.1/GCA_000006825.1_ASM682v1_genomic.fna has 2050 genes
./ncbi_dataset/data/GCA_000006865.1/GCA_000006865.1_ASM686v1_genomic.fna has 2393 genes
./ncbi_dataset/data/GCA_000007125.1/GCA_000007125.1_ASM712v1_genomic.fna has 3171 genes
./ncbi_dataset/data/GCA_000008785.1/GCA_000008785.1_ASM878v1_genomic.fna has 1518 genes
./ncbi_dataset/data/GCA_000091085.2/GCA_000091085.2_ASM9108v2_genomic.fna has 1071 genes
./ncbi_dataset/data/GCF_000006825.1/GCF_000006825.1_ASM682v1_genomic.fna has 2050 genes
./ncbi_dataset/data/GCF_000006865.1/GCF_000006865.1_ASM686v1_genomic.fna has 2393 genes
./ncbi_dataset/data/GCF_000007125.1/GCF_000007125.1_ASM712v1_genomic.fna has 3171 genes
./ncbi_dataset/data/GCF_000008785.1/GCF_000008785.1_ASM878v1_genomic.fna has 1518 genes
./ncbi_dataset/data/GCF_000091085.2/GCF_000091085.2_ASM9108v2_genomic.fna has 1067 genes
./ncbi_dataset/data/GCA_000006745.1/GCA_000006745.1_ASM674v1_genomic.fna has 3622 genes
./ncbi_dataset/data/GCA_000008545.1/GCA_000008545.1_ASM854v1_genomic.fna has 1868 genes
./ncbi_dataset/data/GCA_000008565.1/GCA_000008565.1_ASM856v1_genomic.fna has 3261 genes
./ncbi_dataset/data/GCA_000008725.1/GCA_000008725.1_ASM872v1_genomic.fna has 908 genes
./ncbi_dataset/data/GCA_000027305.1/GCA_000027305.1_ASM2730v1_genomic.fna has 1758 genes
./ncbi_dataset/data/GCF_000006745.1/GCF_000006745.1_ASM674v1_genomic.fna has 3622 genes
./ncbi_dataset/data/GCF_000008545.1/GCF_000008545.1_ASM854v1_genomic.fna has 1868 genes
./ncbi_dataset/data/GCF_000008565.1/GCF_000008565.1_ASM856v1_genomic.fna has 3261 genes
./ncbi_dataset/data/GCF_000008725.1/GCF_000008725.1_ASM872v1_genomic.fna has 908 genes
./ncbi_dataset/data/GCF_000027305.1/GCF_000027305.1_ASM2730v1_genomic.fna has 1758 genes
./ncbi_dataset/data/GCA_000008525.1/GCA_000008525.1_ASM852v1_genomic.fna has 1590 genes
./ncbi_dataset/data/GCA_000008605.1/GCA_000008605.1_ASM860v1_genomic.fna has 1009 genes
./ncbi_dataset/data/GCA_000008625.1/GCA_000008625.1_ASM862v1_genomic.fna has 1777 genes
./ncbi_dataset/data/GCA_000008745.1/GCA_000008745.1_ASM874v1_genomic.fna has 1074 genes
./ncbi_dataset/data/GCF_000008525.1/GCF_000008525.1_ASM852v1_genomic.fna has 1590 genes
./ncbi_dataset/data/GCF_000008605.1/GCF_000008605.1_ASM860v1_genomic.fna has 1009 genes
./ncbi_dataset/data/GCF_000008625.1/GCF_000008625.1_ASM862v1_genomic.fna has 1777 genes
./ncbi_dataset/data/GCF_000008745.1/GCF_000008745.1_ASM874v1_genomic.fna has 1074 genes


q5：
find . -name "*.gff" -exec grep -oP 'Name=\K[^;]+' {} + | sort -u | head -n 5
outp：
./week5-github/bioe/prokka_out_GCA_000006745.1_ASM674v1_genomic/prokka_GCA_000006745.1_ASM674v1_genomic.gff:aaeA
./week5-github/bioe/prokka_out_GCA_000006745.1_ASM674v1_genomic/prokka_GCA_000006745.1_ASM674v1_genomic.gff:aat
./week5-github/bioe/prokka_out_GCA_000006745.1_ASM674v1_genomic/prokka_GCA_000006745.1_ASM674v1_genomic.gff:abgT_1
./week5-github/bioe/prokka_out_GCA_000006745.1_ASM674v1_genomic/prokka_GCA_000006745.1_ASM674v1_genomic.gff:abgT_2
./week5-github/bioe/prokka_out_GCA_000006745.1_ASM674v1_genomic/prokka_GCA_000006745.1_ASM674v1_genomic.gff:accA




