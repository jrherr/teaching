## Some examples of text processing for bioinformatics ##

There's a data deluge right now in biology that is revolutionizing the science.  This data consists of geographic, climate, morphological character, and most pervasively, genomic data.  All of this data is in text formats, but some of these text formats are different.

To work with this data it helps to have some knowledge of the Unix command line and how data can be accessed, queried, and manipulated quickly and efficiently.  Command line tools can process many files at once -- instead of using a GUI to slowly manipulate on file at a time. 

For this brief tutorial, I'll be using some real biological data files found in the data file folder.

The files are:

* *fn554767.fasta*	- this is the sequence data from a bacterial plasmid in fasta format.	

* *fn554767.gff*	- this is the annotated gene data from the bacterial plasmid in gene feature format (gff).

* *synteny_data.sam*    - this is a synteny mapping file showing the presence of shared features in two bacterial samples.

 
## Displaying text with _cat_ command ##

_cat_ is a useful command (name comes from concatenate as it can also be used to combine files, more on that in a minute) which will allow you to display the contents of a file.

We can also use the commands _head_ and _tail_ to look at parts of large data files.

## Searching with _grep_ command ##

_grep_ is a handy tool that we can use for a number of tasks.  _grep_ is command line shorthand for "general regular expression" and can be used for pattern matching (among other things).

	grep -c '^>' fn554767.fasta

The _grep_ command will return the number of DNA sequences in the fasta file - the search term looks for the presence of the > symbol which designates the beginning of a sequence name.  The caret symbol "^" denotes the beginning of a line of text using regular expressions.

You can use _grep_ to "pipe" to other commands such as those I breifly mentioned above -- _head_, _tail_, _sort_, etc. 

## Find & replace with _sed_ ##

Often times we will need to manipulate text files with biological data to play well with other tools that require the data to be in different formats.  Other times it's nice to be able to manipulate a file to be easier to read by a human.

I often find myself using the tool _sed_ (_sed_ is short for "stream editor") to find and replace quickly at the command line.

For example, if we want to replace the abbreviation of "CDS" with "coding" in our gene annotation file, we can type:

	sed 's/CDS/coding/' fn554767.gff

This will replace all occurences of "CDS" with "coding" in our file.  

This can sometimes be a problem as _sed_ overwrites the original text file, so I often make a backup of the original file with the -i flag by typing "-i *.bak" within my command.  I use the "*" because I usually use _sed_ to find & replace on many files at a time.

## Manipulating columns and rows with _awk_ ##

The tool _awk_ gets it's name from the three people who developed it and it's a powerful tool for text processing and data parsing.

For example, if we're looking for all the genetic annotations at the start of the bacterial plasmid, we can search for all annotations of our plasmid by limiting our file to the coding regions between the start and 870 base pairs into our annotation file (columns 4 and 5 in a _gff_ formatted file).

	awk '$4=13&&$5=870' fn554767.gff

_awk_ can be used to select, reorder, swap, and parse column data.
