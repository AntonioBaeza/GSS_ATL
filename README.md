# GSS_ATL
Genome Survey Sequencing in the Alligator Snapping Turtle

![image](https://user-images.githubusercontent.com/47224963/234122516-f5bd0e67-999d-433a-811b-544a5b54fa6b.png)

# Reads Quality Control (fastp)
fastp -i SRR13329724_1.fastq.gz -I SRR13329724_2.fastq.gz -o fastpSRR13329724_1.fastq.gz -O fastpSRR13329724_2.fastq.gz

# Genome Size (KMC k-mer counting)
kmc -k21 -t11 -m64 -ci1 -cs100000 @FILES reads /home/ant/Turtle
kmc_tools transform reads histogram reads21.histo -cx100000

# Genome Size (RESPECT genome size estimation)
respect -d dataTURTLE/ -I dataTURTLE/hist_info.txt -N 11 --debug

# Repetitive Element Analyses
# RepeatExplorer
http://repeatexplorer.org/

# Reads Decontamination (Kraken2)
kraken2 --use-names --db /home/ant/kraken2-microbial-fatfree/ --gzip-compressed --paired fastpSRR13329724_1.fastq.gz fastpSRR13329724_2.fastq.gz --threads 11 --unclassified-out uncseqs#.fastq --report kraken2_report.txt --output kraken2_output.txt


# Mitochondrial Genome Assembly (GetOrganelle)

get_organelle_from_reads.py -1 SRR13329724_1.fastq.gz -2 SRR13329724_2.fastq.gz -t 11 -o SnappingTurtle.mitogenome -F animal_mt -R 10 -s SeedMitogemome.fasta
