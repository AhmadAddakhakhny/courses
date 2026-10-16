# Files - grep (global regular expression print)
```bash
# grep is able to deal with file/s and directory/ies

# grep -c word file-name - shows count of the word in the file
grep -c dbg-msg: handler.log # 109 times
grep -C2 dbg-msg: src.cpp # shows more context around "dbg-msg"

grep -v # this command helps in execluding specific results "use it after pipe
# it's possible to pipe different times, to execlude different patterns,
# !#TBD: search on execluding multiple patterns with one grep -v
grep host sudo_logsrvd.conf | grep -v relayhost # execlude 'relayhost'

# grep with directories
# search under this path with all depth levels
grep -r word /home/ahmed/ # '-r' option should be passed
grep -c /home/ahmed/* # P.S. searches the files only under this path

# execlude a file among files during the grep run
# grep -C4 dbg-msg: file.txt --exclude="file2.txt"

# list the files that matched the search
grep -rl host /home/ahmed

# grep two differnt patterns in one grep
grep -e hostname -e domain file.txt

# grep with regular expression at 16:30 min

## Use case #1:
# list all the possible patters based on a regular expression
# and make the output result filtered, so it doesn't contain
# any dublicates
grep -oE "regex-rule" | sort | uniq 
# unit does the 'set math operation', but the input data should
# be sorted first. 
# -o: print the match pattern only, not the whole line
# -E: use extended regular expression option to avoid the default

## Use Case #2:
# list all the words that came right before this match pattern 'tls'
grep -oP "regex-rult" sudo_logsrvd.conf
- P: use perl regular expression, perl is very advanced in regex
```
## Files - sed (stream editor)
> transforming the input stream
```bash
# sed changes take place only if you passed (-i) option
# without '-i' you will see the change on the terminal only.
# you can do different things with the command

# 1. text replacement
# sed -i "s/regex|word/replacement/" file-name
# sed -i "s/regex|word/replacement/g" file-name # g: change all similar words
# sed -iE "s/extended-regex/replacement/" file-name

# 2. print specific line
sed -n '20p' file.txt # p for print
sed -n '9,12p' file.txt # print from line 9 to 12
sed -n '9p;12p' file.txt # print line 9 and 12

# 3. delete
sed -i '/deleted-word/d' file.txt
sed -i '6d' file.txt # delete line number 6

# 4. performe backup before applying the changes
sed -i.bak "s/ubuntu/void/g" file.txt # file.txt.bak is created
```
## Files - Hard and Soft Links
```bash
# it's a way of doing shortcuts

# 1. hard link
ln file.txt file-hard.txt
ln dir1 dir2 # ERROR!
## note:
# a. both files would have the same inode number # ls -i
# the only possible way to know if the two files are hard-link-ed
# through the inode, and ls -l won't highlight that.
# b. thus, hard link is only possible in the same partition
# c. hard link not allowed for directory
# d. removing the original file, won't affect the linked file. (it's kind of a dublicate file)

# 2. soft link
ln -s file.txt file-soft.txt
ln -s dir1 dir2
## notes:
# a. both files have different inodes
# b. ls -l should symbolically the link between the two files
# c. short link is possible for directory
# d. possible to be used among different partitions
# e. how removing the original file affect the linked file? be broken.
rm file.txt
# file-soft.txt is broken and should be deleted as well.
```

