# Zsh

## Print a Python array from shell command output

```zsh
(){
    setopt local_options extended_glob
    print '[' ${(j;, ;)${(qq)$(ls *(.N))}} ']'
}
```

## Pause a command and view the man

^A, ^K, m, a, n, space, ^Y, enter. Upon exit, ^Y.

## Set a command aside.

^A, ^K. Grab it again with ^Y.

Note: These are readline shortcuts. They’re a bit long but can be bound to something shorter in your `inputrc`.

## 2-d array

Array of variable names that expand to an array of these variables values.

### With `extended_glob`

```zsh
${names/(#m)*/${(P)MATCH}}
```

### Retain empty elements

```zsh
print "${(@)names/(#m)*/${(P)MATCH}}"
```

#### Example

```zsh
local -a letters=(a b c) a=(11 22 33) b=(44 55 66) c=(77 88 99)
print -l -- ${names/(#m)*/${MATCH} => ${(P)MATCH}}
```

```console
a => 11 22 33
b => 44 55 66
c => 77 88 99
```

## Format zsh variables

```zsh
(){
    local pattern="$1"
    typeset -U -m "${pattern}" -p1 "$var"
}
```

```zsh
# sorted
(){
    local pattern="$1"
    for var in $(print -m "${pattern}" ${(oNk)parameters}); do
        typeset -U -p1 "$var"
    done
}
```
```
