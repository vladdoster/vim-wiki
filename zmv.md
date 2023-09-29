# zmv

## replace `_` with `-`

```zsh
zmv '*_*' '${f:gs/_/-}'
```

## lowercase file names

```zsh
zmv -fw '*' '${(QL)1}'
```
