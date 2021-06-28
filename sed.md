= Sed =

====Recursivley replace text in all files====

 grep -rl oldtext . | xargs sed -i 's/oldtext/newtext/g'

====Escape characters in sed====

 :-$HOME\/.config\/bin
