## Introduction to the Bash Shell

### Orientation within the Shell - the most commonly used tools

**pwd** - print working directory

**ls** - list files in a folder or location

examples:

* **ls -a** = lists all the files and folders (shows hidden files in addition to regular list of files)

* **ls -l** = shows detailed list of the files in a location

* **ls -lh** = shows detailed list of files in a location using "human" readable notation

* **ls -l \*.txt** = lists only the "text" files in a location in detail

* **ls -lh <filename>** = shows only files with the name designated as <filename>

Try to learn just one group of commands at a time...


### Movement within the shell file structure

**cd** - change directory

examples: 

* **cd ..** -> change directory to parent folder (one step back)
* **cd ~/user** -> change directory to the user's home folder
* **cd /** -> change directory to the root folder


### Basic Filesystem Operations

**cp** - copy

**mkdir** - make directory (make a folder)

**mv** - move a file or directory to another location

**rm** - remove a file

**rmdir** - remove a directory


mkdir = create new folder
mkdir myStuff ..
mkdir myStuff/pictures/ ..
cp image.jpg newimage.jpg = copy and rename a file
cp image.jpg <folderName>/ = copy to folder
cp image.jpg folder/sameImageNewName.jpg
cp -R stuff otherStuff = copy and rename a folder
cp *.txt stuff/ = copy all of *<file type> to folder
mv file.txt Documents/ = move file to a folder
mv <folderName> <folderName2> = move folder in folder mv filename.txt filename2.txt = rename file
mv <fileName> stuff/newfileName
mv <folderName>/ .. = move folder up in hierarchy
rm <fileName> .. = delete file (s)
rm -i <fileName> .. = ask for confirmation each file rm -f <fileName> = force deletion of a file
rm -r <foldername>/ = delete folder
touch <fileName> = create or update a file