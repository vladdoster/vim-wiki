= Python =

====Start simple HTTP server====

python2
 python -m SimpleHTTPServer

python3
 python -m http.server

====Python deubgger (PDB)====

 python -m pdb my_script.py

**Commands**:
c: continue execution
w: shows the context of the current line it is executing.
a: print the argument list of the current function
s: Execute the current line and stop at the first possible occasion.
n: Continue execution until the next line in the current function is reached or it returns.

====Profile a script====

 python -m cProfile my_script.py

====CSV to JSON====

 python -c "import csv,json;print json.dumps(list(csv.reader(open('csv_file.csv'))))"
 
====pyenv issues====

Python SSL extension isn't compiled

 LDFLAGS=-L/usr/lib/openssl CFLAGS="-DOPENSSL_NO_SSL3 -I/usr/include/openssl" pyenv install -v <desired version>

If Python2, install 2.7.13
