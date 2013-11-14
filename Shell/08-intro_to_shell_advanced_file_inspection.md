### Advanced Looking Around and researching files

find
grep -r
tree

The slow method (sometimes very slow):
locate <text> = search the content of all the files locate <fileName> = search for a file
sudo updatedb = update database of files
find = the best file search tool(fast)
find -name “<fileName>”
find -name “text” = search for files who start with the word text
find -name “*text” = “      “    “    “   end   “    “   “

Advanced Search:
Search from file Size (in ~)
      find ~ -size +10M = search files bigger than.. (M,K,G)
Search from last access
      find -name “<filetype>” -atime -5
“
             ('-' = less than, '+' = more than and nothing = exactly)
Search only files or directory’s
find -type d --> ex: find /var/log -name "syslog" -type d find -type f = files
More info: man find, man locate

df
ps
which