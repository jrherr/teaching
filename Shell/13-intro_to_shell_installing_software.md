## Installing software

When software is available in package repositories then you may install with one command.  
For example, using Ubuntu: sudo apt-get install <nameOfSoftware>
      ex--> sudo apt-get install aptitude

If you download programs from the Internet in .gz format
(or bz2, zip, rar, etc.) - “Compiling from source”

Step 1, create a folder to place the file:
      mkdir /home/username/src <-- then cd to it

Step 2, with 'ls' verify that the file is there
(if not, mv ../file.tar.gz /home/username/src/)

Step 3, decompress the file (if .zip: unzip <file>)
<--

Step 4, use 'ls', you should see a new directory

Step 5, cd to the new directory

Step 6.1, use ls to verify you have an INSTALL file, then: more INSTALL
If you don't have an INSTALL file:

Step 6.2, execute ./configure <-- creates a makefile Step 6.2.1, run make <-- builds application binaries Step 6.2.2 : switch to root --> su

Step 6.2.3 : make install <-- installs the software

Step 7, read the readme file