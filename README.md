# GSS_ATL
Genome Survey Sequencing in the Alligator Snapping Turtle

![image](https://user-images.githubusercontent.com/47224963/234122516-f5bd0e67-999d-433a-811b-544a5b54fa6b.png)

# Reads Quality Control (fastp)


# Mitochondrial Genome Assembly (GetOrganelle)

get_organelle_from_reads.py -1 SRR13329724_1.fastq.gz -2 SRR13329724_2.fastq.gz -t 11 -o OtherSnappingTurtle.mitogenome -F animal_mt -R 10 -s NC_011198.fasta
