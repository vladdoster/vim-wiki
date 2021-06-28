# find

## list directories of `n` depth

```bash
find -maxdepth 2 -type d -ls
```
 
## bulk file rename
  
```bash
find . -depth -name "*.sh" -exec sh -c 'f="{}"; mv -- "$f" "${f//_/-}"' \;
```
