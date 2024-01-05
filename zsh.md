# Zsh

## Print a Python array from shell command output

```zsh
(){
    setopt local_options extended_glob
    print '[' ${(j;, ;)${(qq)$(ls *(.N))}} ']'
}
```
