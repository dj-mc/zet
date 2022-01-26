# bash

## get help

`man %command%`  
`%command% -h/--help/-?`  
`info %command%`  
`help %builtin/keyword%`  
`apropos %something%`

## redirections

`grep "something" < ~/input.txt > ~/output.txt`

## arguments

`$#` number of arguments
`$@` arguments as list of strings
`$*` arguments as single string

```bash
for a in "$@"; do some_thing "$a"; done
```
