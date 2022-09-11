# find

## list directories of `n` depth

```bash
find -maxdepth 2 -type d -ls
```
 
## bulk file rename
  
```bash
find . -depth -name "*.sh" -exec sh -c 'f="{}"; mv -- "$f" "${f//_/-}"' \;
```

## use `>` in an xargs command

> **Note**
> Do not make the mistake of doing thIis:
>
> ```bash
> sh -c "grep ABC {} > {}.out"
> ```

It will error in alot of conditions (i.e., funky filenames, impossible to quote right). 

`{}` must be a separate argument to the command to avoid code injection bugs.

```bash
xargs -I{} sh -c 'grep ABC "$1" > "$1.out"' -- {}
```

### recursive

```bash
find /foo -exec sh -c 'grep "$1" > "$1.out"' -- {} \;
```

### non-recursive

```bash
for file in *; do grep "$file" > "$file.out"; done
```
