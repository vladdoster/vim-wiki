# Makefile

## Get user input

```Make
install: 
    @echo "Proceed with install? [y/N] "; \
    read OPT; \
    echo "$$(OPT) to install"
```

### Pass arguments to a Make target

Method 1:

run: prog
    ./prog $(filter-out $@, $(MAKECMDGOALS))

%:
    @true
filter out current goal from list of goals. create catch all target (%) which does nothing to silently ignore the other goals.

Method 2:

ifeq (run, $(firstword $(MAKECMDGOALS)))
  runargs := $(wordlist 2, $(words $(MAKECMDGOALS)), $(MAKECMDGOALS))
  $(eval $(runargs):;@true)
endif

run:
    ./prog $(runargs)
if the target is run then remove the first goal and create do nothing targets for the remaining goals using eval.

both will allow you to write something like this

$ make run arg1 arg2
