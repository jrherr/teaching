### Working with Archived or Compressed Files

tar

unzip

gzip
gunzip

bzip2

## Archive and compress data Archive and compress data the long way:
Step 1, put all the files you want to compress in
the same folder: ex --> mv *.txt folder/
Step 2, Create the tar file:
tar -cvf my_archive.tar folder/
      -c : creates a .tar archive
      -v : tells you what is happening (verbose)
      -f : assembles the archive into one file
Step 3.1, create gzip file (most current): gzip my_archive.tar
        to decompress: gunzip my_archive.tar.gz
Step 3.2, or create a bzip2 file (more powerful but slow): bzip2 my_archive.tar
        to decompress: bunzip2 my_archive.tar.bz2
step 4, to decompress the .tar file:
       tar -xvf archive.tar archive.tar
Archive and compress data the fast way:
gzip: tar -zcvf my_archive.tar.gz folder/
      decompress: tar -zcvf my_archive.tar.gz Documents/
bzip2: tar -jcvf  my_archive.tar.gz folder/
      decompress: tar -jxvf archive.tar.bz2 Documents/
Show the content of .tar, .gz or .bz2 without decompressing it:
gzip:
      gzip -ztf archive.tar.gz
bzip2:
      bzip2 -jtf archive.tar.bz2
tar:
      tar -tf archive.tar
tar extra:
      tar -rvf archive.tar file.txt = add a file to the .tar
You can also directly compress a single file and view the file
without decompressing:
Step 1, use gzip or bzip2 to compress the file:
      gzip numbers.txt
Step 2, view the file without decompressing it:
zcat = view the entire file in the console (same as cat)
zmore = view one screen at a time the content of the file (same as more) zless = view one line of the file at a time (same as less)