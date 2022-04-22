# bash

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

```bash
$# # number of arguments  
$@ # arguments as list of strings  
$* # arguments as single string
```

```bash
for a in "$@"; do some_thing "$a"; done
```

## arrays

```bash
arr=() # empty array  
arr=(1 2 3) # init array  
${arr[2]} # third element  
${arr[@]} # all elements  
${!arr[@]} # array indices  
${#arr[@]} # array size  
arr[0]=3 # to 1st element  
arr+=(4) # append values  
str=$(ls) # output to string  
arr=( $(ls) ) # output to array  
${arr[@]:i:n} # n elements from index i  
```
