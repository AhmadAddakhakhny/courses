## Navigating Directories
```bash
# the -F option highlights the type of the file/directory of the listed objects
ls -F
ls -lF

# list files/directories with human-readable size
ls -lh
```

## Alias
```bash
# set alias
alias lh='ls -lahF'

# unset alias
unalias lh
```

## Disk usage
```bash
# get size with human-readable form and summary
du -hs

# get dir size
du -hs /dir

# get the size of all dirs under dir 
du -hs /dir/*

# get the size with diretory level/depth
du -hd 1 /var # same as: du -hs /var/*
du -hd 2 /var

# get the size of each file and directory in all levels
du -h
du -h /var
```
## Crete, Delete, copy and move
```bash
# create a child dir under a non-existed parent
mkdir -p parent/child

# copy #1: copy a file and keep original name
cp dir1/file.txt ./dir2/
# copy #2: copy a file and keep change original name
cp dir1/file.txt ./dir2/file-copy.txt
# copy #3: copy a directory to another directory (the copied dir sits under the desintation dir)
cp -r dir2/ dir1
.
├── dir1
│   └── dir2
│       ├── file-copy.txt
│       └── file.txt
└── dir2
    ├── file-copy.txt
    └── file.txt

# copy #4: copy a directory content to another directory (mirror the source in the destination)
cp -r dir2/* dir1/ # -r safes you in case of directories sit under the source dir

# Move: moving dir or files no flag needed like '-r'
mv dir1/file.txt dir2/ # file.txt moves from dir1 to dir2
mv dir1/nested dir2/ # nested dir moves from dir1 to dir2
mv dir2/nested dir2/renamed-nested # renaming directory
mv dir1 dir2 dir3 # move dir1 and dir2 to sit under dir3

# Remove: by default there is no recycle pin in linux, but some distros support it.
rm dir1/file.txt
rm -r dir2/nested # '-r' requred for recursive deletion
rm -rf dir1 # '-f' avoid confirmation response in case the dir contains multiple objects.
```


## Piping, cat, sort, tail, echo and tr
```bash
# cat open one or multible files at the same time
cat file.txt file2.txt

# tail and head: used to print out part of the file (first 10 numbers or more if configured)
tail -f file.txt # watching the file

# sort: by default sorts alphabitical ascendingly, (-r) descendingly.
cat file.txt file2.txt | sort -r

# echo: to print a string whether hardcoded or in a variable,
# and (-e) shows that the command contains special characters,
# mostly with coloring.

# ANSI escape codes (check the documentations)
# HOMEPAGE: https://gist.github.com/fnky/458719343aabd01cfb17a3a4f7296797
echo -e "\e[38;5;82mHello from terminal\e[0m"

\e - escape char .. the following is instruction not a string
[- beginning of the format instruction
38 - set foreground color
5 - color refrence is 255 (a lookup table) not RGB based
82 - color id in the lookup table (green)
m - end of instruction
\e[0m - reset the format instruction (if no reset, terminal would keep using this color forever)

# tr: translation, as it transform the text
echo "hi from terminal" | tr 'a-z' 'A-Z' # make it  all CAPS
echo "hi from terminal" | tr -d 'hi' # delete any h, i chars in the text
echo "my phone number is 0123456789 call me later" | tr -cd '0-9\n' # delete any thining except the numbers 0-9
```

