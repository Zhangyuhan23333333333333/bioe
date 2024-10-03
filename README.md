#bioe

安装week4-5用的软件包：
conda install -c bioconda prodigal prokka

week4-5：

q1：
cd /home/zhany0y/fond_of_bioe/week5-github/bioe/
python week5-q1.py

protseq="KVRMFTSELDIMLSVNGPADQIKYFCRHWT*"
a="The number of amino acids in the encoded peptide (not including the stop codon) is "
b="The open reading frame of the DNA sequence encoding the amino acids (including the stop codon) contains "
print(a+str(len(protseq)-1)+".")
print(b+str(len(protseq)*3)+" bases.")

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

#!/bin/bash
output_file="gene_annotation_summary.txt" # 保存.fna的注释基因数量
echo "File Name | Annotated Gene Count" > $output_file
max_genes=0
max_genes_file=""
find . -name "*.fna" | while read fna_file; do  # 当前目录，子目录下的.fna
    file_name=$(basename "$fna_file") # 无路径纯文件名
    output_gff="${file_name%.fna}.gff" #临时输出for each .fna
    prodigal -i "$fna_file" -o "$output_gff" -f gff #prodigal注释
    gene_count=$(grep -c -w "CDS" "$output_gff") # 注释的基因(cds)数量
    echo "$file_name | $gene_count" >> $output_file
    rm "$output_gff"
done


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


# !/bin/bash
FILES=$(find . -name "*.fna") #所有.fna文件
for file in $FILES; do
    OUTPUT="prokka_out_$(basename "$file" .fna)" #输出目录名称，无扩展文件名为后缀
    PREFIX="prokka_$(basename "$file" .fna)" #前缀，同上
    prokka --outdir "$OUTPUT" --prefix "$PREFIX" "$file" --quiet #prokka之，静默
    num_genes=$(grep -c "CDS" "$OUTPUT/$PREFIX.gbk") #输出到gbk    
    echo "$file has $num_genes genes" >> prokka_counts.txt #print gbk
done


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




