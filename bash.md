# bash

## todo

`curl -O <url>`  
`curl -o- <url>`  
`wget -P <url>`  
`tar -xvjf <file>`

## get help

`man %command%`  
`%command% -h/--help/-?`  
`info %command%`  
`help %builtin/keyword%`  
`apropos %something%`

## redirections

```bash
grep "something" < ~/input.txt > ~/output.txt
```

## arguments

`$#` number of arguments  
`$@` arguments as list of strings  
`$*` arguments as single string

```bash
for a in "$@"; do some_thing "$a"; done
```
