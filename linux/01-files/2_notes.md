## Redirection - Standard Input, Output and Error
> Any process being created will have 3 main files under its fd (file descriptor)"proc/id/fd",
0 - stdin (the process listens to this file)
1 - stdout (the process outputs its result to this file)
2 - stderr (the process outputs its error-results to this file)

### Redirect operator (> , >>), stadout redirection
```bash
echo "hello world!" > file.txt # Overrides file content
echo "hello again!" >> file.txt # Appends to the file content
```

### Input redirect operator 
#### single operator (<)
```bash
# its usage not very often, and deals with the commands that accepts only
# input from stdin (input redirect operator)  or as a work around from pipes
# ex. "tr" "wc"
tr 'a-z' 'A-Z' < file.txt
wc < file.txt # the result output is a bit cleaner
```
#### double operator (<<) "here document cmd"
```bash
# it's being used with commands that expect file/s as an input "i.e. cat",
# but you want to input just a string, but there is a rule:
# 1. string should be multiline
# 2. the first and last word should be the same "delimiter" and commonly know "EOF"
cat << EOF
> Hello
> World!
> EOF
result:
Hello
World!

# redirect the text to a file through cat cmd:
cat << EOF > file.txt
> Hello
> World!

```

#### triple operator (<<<) here string
```bash
# similar to "here document cmd, but the sting shouldn't contain multilines
wc -c <<< "here string example"
# note: it's not POSIX, it works only on bash.
```

### stderr redirection
```bash
# in simple words the ">" operator redirects only the stdout result,
# but in case of errors, you should redirect the stderr.
ls hi 2> file.txt # overrides file content
ls hi 2>> file.txt # append to the file content
```
#### Redirect stdin and stderr together to a file (&>)
```bash
ls hi &> file.txt
ls hi > file.txt 2>&1 # same but un-common
ls hi > file.txt 2> file.txt # more exciplicit and readable
ls hi > file.txt 2> file-err.txt # redirect to two files
```
#### /dev/null
```bash
#  it's used to redirect unwanted result to it, and the kernel would respond by success
ls hi 2> /dev/null
```
---
