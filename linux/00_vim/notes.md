## VIM Modes

```vim
- 1 Normal mode
- 2 Insert mode
- 3 Command mode 
```

### Arrows
```vim
- left(h), down(j), up(k), right(l) - you can prepend a number to make a step > 1

- first line of the file (gg), last line (shift + g), or specific line (line-no + shift + g)
```
### curser positioning in line
```vim
- go to the beinning of the line (NM: 0)
- go to the end of the line (NM: $)
- go to the first character in the line (NM:under-score: _)
- go to the right word by word (NM: w)
- go to the left word by word (NM: b)

```

### Delete and Undo
```vim
- delete a char (delete button) (NM: x)
- delete a char (backspace button) (NM: X)
- undo (NM: u)
- re-do (NM: ctrl + r)

- delete a line (NM: dd)
- delete a front word (NM: dw)
- delete a backward word (NM: db)
- delete N lines -> current and N-below (NM: d3j)
- delete N lines -> current and N-above (NM: d3k)
- delete from midle of the line till the end (NM: d$)
- delete from midle of the line till the front (NM: d0)

- undo everything since the file got opened first time (:e!)
```


### copy(yank) and paste
```vim
- copy a line (NM: y)
- paste a line (NM: p)

# same compination shall be applied
- copy a front word (NM: yw)
- copy a backward word (NM: yb)
- copy from the middle till the end (NM: y$)
- copy from the middle till the front (NM: y0)

- note: the (NM: dd) shall be considered as 'cut' so you can paste it. 
```

### Search
```vim
- search after the curser (NM: /search_word + enter)
- search before the curser (NM: ?search_word + enter)
- to navigate the matched words use next (NM: n or N) front or back
```

## VIM Modes
```vim
#1 insert mode
1. (IM: i) enter insert mode, start writing before the curser
2. (IM: a) enter insert mode, start writing after the curser (logically more used)

#2 command mode
- (CM: :) enter Command Mode
- exit without save (:q!)
- exit  and save (:x)
- show line numbers (:set number)

#3 visual mode
1. visual block (NM: ctrl+v -VM block)
2. visual line (NM: shift+v -> VM line)
```

## .vimrc configs
> any command runs temporary, better store vim configs in .vimrc
```vim
set number
```
