## Chapter 0

```
u       ->  undo the latest change
Esc     ->  enter mode command
```

## Chaper 1

```
h       ->  moves left
l       ->  moves right
j       ->  moves down
k       ->  moves up
```
```
:q!     ->  quits editor and discard changes
x       ->  delete the character under the cursor
```
```
i       ->  insert mode
A       ->  append text
```
```
:wq     ->  write a file and quit

## Chapter 2 

```
dw      ->  delete a word
d$      ->  delete to the end of the line
```
```
list of motions:
w       -> until the end of the line excluding its first character
e       -> to the end of the current word including the last character 
$       -> to the enf of the line including the last character
```
```
2w      ->  move the cursos two words forward
3e      ->  move the cursos to the end of the third word forwawrd
0       ->  move the start of the line
```
```
dw2     ->  delete the 2 consecutive words
dd      ->  delete a whone line
2dd     ->  delete two lines
```
```
u       ->  undo the last commands
U       ->  fix a whole line
<C-r>   ->  redo the commands
```

### Chapter 3:

```
p       ->  put the line from clip below the cursor
P       ->  put the line from clip after the cursor
```
```
rx      ->  replace the character at the cursor with x
ce      ->  change until teh end of a word
c       ->  used with the same motion as deleted (w, e, $)
```

### Chapter 4: 

```
<C-g>   ->  show location in the file
G       ->  move to the bottom of the file
gg      ->  move to the start of the file
3G      ->  move to the line 3
```
```
/       ->  search a word
n       ->  search the last phrase again
N       ->  search the last phrase in the opposite direction
```
```
%       ->  find a matching ), ], }
```
```
:s/old/new      ->  changed the first match of "old" with "new" in the line
:s/old/new/g    ->  substitute globally in the line
:#,#s/old/new/g ->  change every ocurrence of a character string betwen two lines # and #
:%s/old/new/g   ->  substitute globally in the whole file 
:%s/old/new/gc  -> find every ocurrence in the whole file with a prompt wheter to substitute or not
```

### Chapter 5

```
:! <command>    -> execute a command in vim
:w              -> save changes made to the text
```
```
v               -> highlighted text
:r <file>       -> retrieve content of a file
```

### Chaper 6

```
o       -> open a line below the cursos and place in insert mode
O       -> open a line above the cursor and place in insert mode
a       -> insert text after the cursor
```
```
R       -> replace more than one character
```
```
y       -> copy text
```
```
<C-w>   -> jump to another window
<C-d>   -> see possible completitions
```
