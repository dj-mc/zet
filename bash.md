# bash

## get help

`man %command%`  
`%command% -h/--help/-?`  
`info %command%`  
`help %builtin/keyword%`  
`apropos %something%`

```bash
grep "something" < ~/input.txt > ~/output.txt
```

`$#` number of arguments
`$@` arguments as list of strings
`$*` arguments as single string

```bash
for a in "$@"; do some_thing "$a"; done
```
