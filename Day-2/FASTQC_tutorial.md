FASTQC Tutorial
================

Download Fastq files
```
mkdir ~/workdir/fqData && cd ~/workdir/fqData
wget https://de.cyverse.org/dl/d/3CE425D7-ECDE-46B8-AB7F-FAF07048AD42/samples.tar.gz
tar xvzf samples.tar.gz
```

Install the software
```
source activate ngs1
conda install -c bioconda fastqc 
conda install -c bioconda multiqc 
```

Run the FASTQC for each read end
```
mkdir ~/workdir/FASTQC_tut && cd ~/workdir/FASTQC_tut
for f in ~/workdir/fqData/*.fq.gz;do
fastqc -t 1 -f fastq -noextract $f;done
```

Merge the output reports into one super report
```
multiqc -z -o . .
```

