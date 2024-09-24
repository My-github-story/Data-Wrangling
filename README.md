## Copy the files to your home directory on IBEX. Uncompress the zip file on IBEX.
Ans - ```scp /Users/khant0a/Downloads/ncbi_dataset.zip khant0a@ilogin.ibex.kaust.edu.sa:/home/khant0a/```

What is the largest and what is the smallest genome in the ones
you just downloaded.
Ans- $ cut -f 1,11 data_summary.tsv | tail -n+2 | sort -n -u | head -n 1 > largest_genome
$ cat largest_genome
output- Vibrio cholerae O1 biovar El Tor str. N16961	4033464

$ cut -f 1,11 data_summary.tsv | tail -n+2 | sort -t$'\t' -n -k2 | head -n 1
output- Chlamydia trachomatis D/UW-3/CX	1042519

$ cut -f 1,11 data_summary.tsv | tail -n+2 | sort -t$'\t' -n -k2 | head -n 1 | awk '{print $NF}'
output- 1042519

$ cut -f 1,11 data_summary.tsv | tail -n+2 | sort -t$'\t' -n -k2 | tail -n 1 | awk '{print $NF}'
output- 4033464

Find the number of genomes that contain at least two “c” in
the species name. How many of the species names contain two or more
“c” but do not contain the word “coccus”? Your command should be a
single line and output a number

Ans-$ cut -f 1 ncbi_dataset.tsv |tail -n+2 | uniq | grep -ic  "c.*c"
output- 7
$ cut -f 1 ncbi_dataset.tsv |tail -n+2 | uniq | grep -io  "c.*c" | grep -ivc "coccus"
output- 5

Use the find command to find all genome files (FASTA) larger
than 3 megabyte. How many are there (output only the number).
Ans- $ find . -name '*.fna' -size +3M | wc -l 
output- 6

