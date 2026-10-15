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

