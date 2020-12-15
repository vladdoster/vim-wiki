# Makefile

## Get user input

```Make
install: 
    @echo "Proceed with install? [y/N] "; \
    read OPT; \
    echo "$$(OPT) to install"
```
