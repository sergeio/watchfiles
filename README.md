watchdir
========

Execute a command when any file from STDIN is modified

Example usage:
--------------
```
find tests/ src/ -type f | watchdir make test
```
