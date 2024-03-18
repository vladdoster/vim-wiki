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
