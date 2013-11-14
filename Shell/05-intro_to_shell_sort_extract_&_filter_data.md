### Extract, sort and filter data

grep <someText> <fileName> = search for text in file
      -i = Doesn't consider uppercase words
      -I = exclude binary files
grep -r <text> <folderName>/ = search for file names
      with occurrence of the text
With regular expressions:
grep -E ^<text> <fileName> = search start of lines with the word text
grep -E <0-4> <fileName> =shows lines containing numbers 0-4 grep -E <a-z A-Z> <fileName> = retrieve all lines with alphabetical letters
sort = sort the content of files
sort <fileName> = sort alphabetically
sort -o <file> <outputFile> = write result to a file
sort -r <fileName> = sort in reverse
sort -R <fileName> = sort randomly
sort -n <fileName> = sort numbers
wc = word count
wc <fileName> = nbr of line, nbr of words, byte size
      -l (lines), -w (words), -c (byte size), -m
      (number of characters)
cut = cut a part of a file
-c --> ex: cut -c 2-5 names.txt
      (cut the characters 2 to 5 of each line)
-d (delimiter)  (-d & -f good for .csv files)
-f (# of field to cut)
more info: man cut, man sort, man grep

cut
expand
md5sum
sort
tr
uniq

## Flow redirection

Redirect results of commands:
'>' at the end of a command to redirect the result to a file
      ex --> ps -ejH > process.txt
'>>' to redirect the result to the end of a file
Redirect errors:
'2>' at the end of the command to redirect the result to a file
      ex --> cut -d , -f 1 file.csv > file 2> errors.log
'2>&1' to redirect the errors the same way as the standard output
Read progressively from the keyboard
<Command> << <wordToTerminateInput>

Chain commands
'|' at the end of a command to enter another one
      ex --> du | sort -nr | less