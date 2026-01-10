# Python

## Isort

```
isort \
  --force-sort-within-sections \
  --multiline BACKSLASH_GRID \
  --line-length 120 \
  --force-alphabetical-sort-within-sections
```

## Start simple HTTP server

```bash
python -m http.server
```

## Python deubgger (PDB)

```bash
python -m pdb my_script.py
```

### Commands

- c: continue execution
- w: shows the context of the current line it is executing.
- a: print the argument list of the current function
- s: Execute the current line and stop at the first possible occasion.
- n: Continue execution until the next line in the current function is reached or it returns.

## Profile a script

```bash
python -m cProfile my_script.py
```

## CSV to JSON

```bash
python -c "import csv,json;print json.dumps(list(csv.reader(open('csv_file.csv'))))"
```
 
## Pyenv issues

### Python SSL extension isn't compiled

```bash
LDFLAGS=-L/usr/lib/openssl \
CFLAGS="-DOPENSSL_NO_SSL3 -I/usr/include/openssl" \
  pyenv install -v <desired version>
```
