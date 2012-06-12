watchfiles
========

Execute a command when any file from STDIN is modified

Example usage:
--------------
```
find tests/ src/ -type f -name '*.py' | watchfiles make test
```
Will run 'make test' anytime any python file in tests/ or src/ is modified
