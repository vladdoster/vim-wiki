# Bash

## avg-time

Calculate a commands mean runtime over N runs
       
```bash
avg-time [N RUNS]... [COMMAND]...
```

### Example:

```bash
avg_time 5 sleep 1

real 1.000000
user 0.000000
sys 0.000000
```

### Code
	
```bash
avg_time() {
	n=$1
	shift
	(($# > 0)) || return # bail if no command given
	for ((i = 0; i < n; i++)); do
		{ time -p "$@" &>/dev/null; } 2>&1 # ignore the output of the command
		# but collect time's output in stdout
	done | awk '
        /real/ { real = real + $2; nr++ }
        /user/ { user = user + $2; nu++ }
        /sys/  { sys  = sys  + $2; ns++}
        END    {
                 if (nr>0) printf("real %f\n", real/nr);
                 if (nu>0) printf("user %f\n", user/nu);
                 if (ns>0) printf("sys %f\n",  sys/ns)
               }'
}
```

## Silence stdout

```bash
scriptname >/dev/null
```

## Silence stdout && stderr

```bash
scriptname &>/dev/null
