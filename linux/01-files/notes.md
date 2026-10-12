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
