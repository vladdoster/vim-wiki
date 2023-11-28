# Sed

## Recursivley replace text in all files

```bash
grep -rl oldtext . | xargs sed -i 's/oldtext/newtext/g'
```

## Escape characters in sed====

```bash
 :-$HOME\/.config\/bin
```

## Printing lines between two boundaries including both boundaries

```bash
sed -n '/DATA BEGIN/, /DATA END/p' input.txt
```
