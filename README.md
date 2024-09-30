# bioe

安装week4-5用的软件包：
conda install -c bioconda prodigal prokka

问题2：
选取ncbi数据集中的一个基因组，改名为test.fna
prodigal -i test.fna -o genes.gff输出基因信息到gff文件
grep -c "CDS" genes.gff找到被注释的基因数量

问题3：
refer to q3.sh




