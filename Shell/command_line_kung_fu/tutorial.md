## Text Processing 

### Introduction

In this tutorial, I put together some Linux/Unix commands that I found useful for a day-to-day text processing task.

I did not cover all basic functionality of each tool because you will always find tutorials and basic examples online. I also assume that you are slightly familiar with Linux/Unix command line toos such as pipe, redirection, etc.

### Display text with cat command

`cat` is a very simple command you can use to display content in a file. Simply run:
```
cat sample.txt
```
will display all content in sample.txt file.
```
chr1    1000    2000    gene    +
chr1    1000    2000    exon    +
chr2    2000    3400    exon    +
chr2    3000    5000    exon    +
chr3    3001    5002    exon    +
chr12   1000    2000    gene    +
chr12   1000    2000    intron  +
```

You can also run:
```
cat -T -e sample.txt
```
to display tab and the end of line characters. This is helpful when you need to investigate the file format.
```
chr1^I1000^I2000^Igene^I+$
chr1^I1000^I2000^Iexon^I+$
chr2^I2000^I3400^Iexon^I+$
chr2^I3000^I5000^Iexon^I+$
chr3^I3001^I5002^Iexon^I+$
chr12^I1000^I2000^Igene^I+$
chr12^I1000^I2000^Iintron^I+$
```
You can also run:
```
cat - sample.txt
```
then type some texts and hit Ctrl-D to add texts to the beginning of sample.txt.

### Manipulate columns and rows with awk

`awk` accepts conditional expressions that you can use to select or filter data in a text file.
```
awk '$2>=2000&&$3<=4000' sample.txt
```
will select rows of which the second and third columns have a value between 2000 to 3000.
```
chr2    2000    3400    exon    +
```
You can also give `awk` a pattern to search for.
```
awk '/chr3/' sample.txt
```
will search for rows that contain chr3.
```
chr3    3001    5002    exon    +
```
To search for a match in a specific column use:
```
awk '$4 ~/gene/' sample.txt
```
`awk` will select rows that contain "gene" in the 4th column.
```
chr1    1000    2000    gene    +
chr12   1000    2000    gene    +
```
To print out specific columns use:
```
awk '{print $1,$2,$3}' sample.txt
```
Only 1st, 2nd and 3rd columns are printed.
```
chr1 1000 2000
chr1 1000 2000
chr2 2000 3400
chr2 3000 5000
chr3 3001 5002
chr12 1000 2000
chr12 1000 2000
```
You can also use print command to swap the columns. For example,
```
awk '{print $2,$3,$1}' sample.txt
```
will swap column 1 and column 2.
```
1000 2000 chr1
1000 2000 chr1
2000 3400 chr2
3000 5000 chr2
3001 5002 chr3
1000 2000 chr12
1000 2000 chr12
```

### Search with grep

With `-c` option, grep displays the number of lines that contain a search word. We can use this option to count sequences in FASTA format.
```
grep -c '^>' par.fa
```
There are five sequences in par.fa. "^" means the beginning of the line.
```
5
```
By default, grep will also a substring, therefore
```
grep chr1 sample.txt
```
will match both "chr1" and "chr12".
```
chr1    1000    2000    gene    +
chr1    1000    2000    exon    +
chr12   1000    2000    gene    +
chr12   1000    2000    intron  +
```
If you only want to search for "chr1", you need to add -w option. In this case, grep will only search for a whole word that matches the search word.
```
grep -w chr1 sample.txt
```

```
chr1    1000    2000    gene    +
chr1    1000    2000    exon    +
```
You can also search for more than one keywords using `-e` option.

```
grep -e gene -e intron sample.txt
```
will search for lines that contain either "gene" or "intron".

```
chr1    1000    2000    gene    +
chr12   1000    2000    gene    +
chr12   1000    2000    intron  +
```
You can also use OR operator to do the same thing.
```
grep 'gene\|intron' sample.txt
```
Or you can use `egrep`.
```
egrep 'gene|intron' sample.txt
```
grep also accepts AND operator. To search for "chr1" and "gene" run:
```
grep -E "chr1\s.*gene" sample.txt
```
You will get:
```
chr1    1000    2000    gene
```
To do invert search, use `-v` option. For example,
```
grep -v exon sample.txt
```
will exclude any line that has exon in it.
```
chr1    1000    2000    gene    +
chr12   1000    2000    gene    +
chr12   1000    2000    intron  +
```
With `-l` option, `grep` will display a filename instead of a line that contain the search word.
```
grep -l chr12 *
```
will give:
```
sample.txt
```
witn `-c`, `grep` will also display the number of lines that contain the search word in a file.
```
grep -c chr12 *
```
You will get:
```
sample2.txt:0
sample3.txt:2
sample4.txt:0
sample.txt:2
```
With `-n`, `grep` will display a line number and a line that contain the search word.
```
grep -n chr12 sample.txt
```
will give:
```
sample3.txt:6:chr12,,,,1000,,,,2000,,,,gene,,,,,,+
sample3.txt:7:chr12,,,,1000,,,,,,,2000,,,,intron,,,,+
sample.txt:6:chr12  1000    2000    gene    +
sample.txt:7:chr12  1000    2000    intron  +
```

### Search and substitute with sed

To substitue a word/pattern use,
```
sed 's/chr/scaffold/' sample.txt
```
`sed` will substitute "chr" with "scaffold".
```
scaffold1   1000    2000    gene    +
scaffold1   1000    2000    exon    +
scaffold2   2000    3400    exon    +
scaffold2   3000    5000    exon    +
scaffold3   3001    5002    exon    +
scaffold12  1000    2000    gene    +
scaffold12  1000    2000    intron  +
```
You can also remove a word by substituting it with a blank.
```
sed 's/chr//' sample.txt
```
You will get:
```
1   1000    2000    gene    +
1   1000    2000    exon    +
2   2000    3400    exon    +
2   3000    5000    exon    +
3   3001    5002    exon    +
12  1000    2000    gene    +
12  1000    2000    intron  +
```
To add a word to the beginning of the line use:
```
sed 's/^/chr/' sample2.txt
```
sample2.txt original content is
```
1   1000    2000    gene    +
1   1000    2000    exon    +
2   2000    3400    exon    +
2   3000    5000    exon    +
3   3001    5002    exon    +
12  1000    2000    gene    +
12  1000    2000    intron  +
```
with the above command, you will get:
```
chr1    1000    2000    gene    +
chr1    1000    2000    exon    +
chr2    2000    3400    exon    +
chr2    3000    5000    exon    +
chr3    3001    5002    exon    +
chr12   1000    2000    gene    +
chr12   1000    2000    intron  +
```

### Translate with tr

I rarely use this command, but it can be used to deal with messed up csv or spece/tab delimited files. For example, you are handed a file with this format:
```
chr1,,,,,,1000,,,,2000,,,,gene,,,,+
chr1,,,,1000,,,,,,,,2000,,,,exon,,,,+
chr2,,,,2000,,,,3400,,,,exon,,,,+
chr2,,,,3000,,,,,,,5000,,,,exon,,,,,,,+
chr3,,,,3001,,,,5002,,,,exon,,,,+
chr12,,,,1000,,,,2000,,,,gene,,,,,,+
chr12,,,,1000,,,,,,,2000,,,,intron,,,,+
```
You can try to use awk to print the first three columns.
```
awk -F',' '{print $1,$2,$3}'
```
But here is what you get.
```
chr1  
chr1  
chr2  
chr2  
chr3  
chr12  
chr12
```
`awk` fails to recognize the columns. You can also try to use ",,,," instead.
```
awk -F',,,,' '{print $1,$2,$3}' sample3.txt
```
but you still cannot get rid of all commas.
```
chr1 ,,1000 2000
chr1 1000 
chr2 2000 3400
chr2 3000 ,,,5000
chr3 3001 5002
chr12 1000 2000
chr12 1000 ,,,2000
```
Now we can try using `tr` to collapse multiple commas into one and replace it with a tab.
```
tr -s ',' '\t' < sample3.txt | cat -Te
```
The output is piped to cat command to display a tab character.
```
chr1^I1000^I2000^Igene^I+$
chr1^I1000^I2000^Iexon^I+$
chr2^I2000^I3400^Iexon^I+$
chr2^I3000^I5000^Iexon^I+$
chr3^I3001^I5002^Iexon^I+$
chr12^I1000^I2000^Igene^I+$
chr12^I1000^I2000^Iintron^I+$
```
You can see that multiple commas are converted to a single tab.

`tr` can be used to convert other texts, for example:
```
echo "accggtgt" | tr a-z A-Z
```
will convert lowercase letters to uppercase letters.
```
ACCGGTGT
```
Or we can use it to convert a soft mask in genome sequence to a hard mask.
```
echo "AAAGGTTGAGAGGTGCCaccggtgtCCCAAGGTTTT" | tr a-z X
```
Here is what you will get:
```
AAAGGTTGAGAGGTGCCXXXXXXXXCCCAAGGTTTT
```

### Merge data with paste and join command

`paste` command can be used to append columns from one file to another. For example, sample.txt contains:
```
chr1    1000    2000    gene    +
chr1    1000    2000    exon    +
chr2    2000    3400    exon    +
chr2    3000    5000    exon    +
chr3    3001    5002    exon    +
chr12   1000    2000    gene    +
chr12   1000    2000    intron  +
```
and sample4.txt contains:
```
1000
1000
3000
5000
2000
3000
6000
```
We can add data from sample4.txt to sample.txt as the sixth column by the following command:
```
paste sample.txt sample4.txt
```
Here is the output:
```
chr1    1000    2000    gene    +   1000
chr1    1000    2000    exon    +   1000
chr2    2000    3400    exon    +   3000
chr2    3000    5000    exon    +   5000
chr3    3001    5002    exon    +   2000
chr12   1000    2000    gene    +   3000
chr12   1000    2000    intron  +   6000
```
`join` command works like the `paste` command except that two files have to share a common column. For example, genes1.txt contain a list of genes with their expression levels like this:
```
GNBP3   3400
GNBP1   50
Toll    1230
Spatzle 2300
dorsal  57000
Dmik2   34000
```
And genes2.txt contains the same list of genes with different expression levels. We can merge them together to get a list of genes with expression levels from two datasets with `join`.
```
join genes1.txt genes2.txt
```
You will get:
```
GNBP3 3400 400
GNBP1 50 30050
Toll 1230 1240
Spatzle 2300 4400
dorsal 57000 87000
Dmik2 34000 14000
```
It works because genes_1.txt and genes_2.txt have a common column.

`join` command still works if the data are missing. For example:
```
join genes_1.txt genes_3.txt
```
will give:
```
GNBP3 3400 400
GNBP1 50 30050
Toll 1230 
Spatzle 2300 4400
dorsal 57000 87000
Dmik2 34000 14000
```
In this case, the expression of Toll gene in genes3.txt is missing.

We can use `-e` STRING to replace a missing value with STRING. For example,
```
join -e NA genes1.txt genes3.txt
```
the missing value is replaced by "NA".
```
GNBP3 3400 400
GNBP1 50 30050
Toll 1230 NA
Spatzle 2300 4400
dorsal 57000 87000
Dmik2 34000 14000
```

## Important tools

### `bioawk` tutorials

#### Concepts

Don't write your own FASTA/FASTQ parsers! FASTA is much easier, but
*code reuse* is important here. FASTQ is a very hard format to parse
*safely* and *quickly*. See
[this post](http://www.biostars.org/p/10353/#11256) for more info on
how tricky it can be to parse FASTQ.

Heng Li (author of samtools, bwa) has written a nice set of parsers
for different languages called
[readfq](https://github.com/lh3/readfq). bioawk is also a tool of Heng
Li's too. 

#### Installing `bioawk`

For this quick tutorial, let's just clone bioawk and install it to
your `/usr/local/bin/`:

    git clone git://github.com/lh3/bioawk.git && cd bioawk && make && mv awk bioawk && sudo cp bioawk /usr/local/bin/

#### `bioawk` Concepts

Bioawk is just like awk, but instead of working with mapping columns
to variables for you, it maps bioinformatics field formats (like
FASTA/FASTQ name and sequence).

You can count sequences very effectively with bioawk, because awk
updates the built-in variable `NR` (number of records):

    bioawk -cfastx 'END{print NR}' test.fastq

But this is just the beginning; what if you wanted to use it to make a
tab-delimited table of names and sequence lengths, you could do:

    bioawk -cfastx '{print $name, length($seq)}' test-trimmed.fastq

Or maybe you want to see how many sequences are shorter (less than
80bp) now?

    bioawk -cfastx 'BEGIN{ shorter = 0} {if (length($seq) < 80) shorter += 1} END {print "shorter sequences", shorter}' test-trimmed.fastq
    
bioawk can also take other input formats: 

    bed:
         1:chrom 2:start 3:end 4:name 5:score 6:strand 7:thickstart 8:thickend 9:rgb 10:blockcount 11:blocksizes 12:blockstarts
    sam:
        1:qname 2:flag 3:rname 4:pos 5:mapq 6:cigar 7:rnext 8:pnext 9:tlen 10:seq 11:qual
    vcf:
        1:chrom 2:pos 3:id 4:ref 5:alt 6:qual 7:filter 8:info
    gff:
        1:seqname 2:source 3:feature 4:start 5:end 6:score 7:filter 8:strand 9:group 10:attribute
    fastx:
        1:name 2:seq 3:qual 4:comment

## `seqtk`

Seqtk is for processing sequences in the FASTA or
FASTQ format. It seamlessly parses both FASTA and FASTQ files which can also be
optionally compressed by gzip.

Seqtk Examples
--------------

* Convert FASTQ to FASTA:

        seqtk seq -a in.fq.gz > out.fa

* Convert ILLUMINA 1.3+ FASTQ to FASTA and mask bases with quality lower than 20 to lowercases (the 1st command line) or to `N` (the 2nd):

        seqtk seq -aQ64 -q20 in.fq > out.fa
        seqtk seq -aQ64 -q20 -n N in.fq > out.fa

* Fold long FASTA/Q lines and remove FASTA/Q comments:

        seqtk seq -Cl60 in.fa > out.fa

* Convert multi-line FASTQ to 4-line FASTQ:

        seqtk seq -l0 in.fq > out.fq

* Reverse complement FASTA/Q:

        seqtk seq -r in.fq > out.fq

* Extract sequences with names in file `name.lst`, one sequence name per line:

        seqtk subseq in.fq name.lst > out.fq

* Extract sequences in regions contained in file `reg.bed`:

        seqtk subseq in.fa reg.bed > out.fa

* Mask regions in `reg.bed` to lowercases:

        seqtk seq -M reg.bed in.fa > out.fa

* Subsample 10000 read pairs from two large paired FASTQ files (remember to use the same random seed to keep pairing):

        seqtk sample -s100 read1.fq 10000 > sub1.fq
        seqtk sample -s100 read2.fq 10000 > sub2.fq

* Trim low-quality bases from both ends using the Phred algorithm:

        seqtk trimfq in.fq > out.fq

* Trim 5bp from the left end of each read and 10bp from the right end:

        seqtk trimfq -b 5 -e 10 in.fa > out.fa

## `fastx-toolkit`

[fastx-toolkit](http://hannonlab.cshl.edu/fastx_toolkit/)

## `fastq-tools`

[fastq-tools](http://homes.cs.washington.edu/~dcjones/fastq-tools/)

## piping to subsample fastq

Let's put what we have learned so far into use:

```
#! /bin/bash

# trim centralia sequences so we can test pipeline and analysis

# use pandaseq to merge reads - requires name list (file <list.txt> in same folder as this script) of forward and reverse reads to be merged using the panda-seq program

for file in $(<list.txt)
do
  pandaseq -f ${file}_L001_R1_001.fastq.gz -r ${file}_L001_R2_001.fastq.gz -A pear -w assembled_reads/${file}.fasta -g assembled_reads/${file}.log
done

cat assembled_reads/{file}.fasta |\
awk '/^>/ { if(i>0) printf("\n"); i++; printf("%s\t",$0); next;} {printf("%s",$0);} END { printf("\n");}' |\
perl -MList::Util -e 'print List::Util::shuffle <>' |\
head -n 30000 |\
awk '{printf("%s\n%s\n",$1,$2)}' > ./{file}_subsambple.fasta
#end
```
