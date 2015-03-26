Watchfiles
==========

Execute a command when any watched file is modified.

This project is probably one of the shortest, simplest things I've put on
github, and maybe the one that gives me the most joy.  I use it almost daily.


Why?
----

Coding, I found myself constantly popping back into a terminal to execute the
same command over and over again.  I didn't want it to run it in a loop, as
that invariably causes my CPU fans to spin up and threaten takeoff.  With an
added sleep, the waiting got too annoying.

I wanted something like the `watch` command.  But instead of watching the
output of a command, I wanted it to watch my files, and do something when I
made a change.

Linux has Inotify, and OSX has its own thing.

But watchfiles is flexible, cross-platform, and very easy to use.


Example usage:
--------------
```
find tests/ src/ -type f -name '*.py' | watchfiles 'make test && make doc'
```
Will run 'make test && make doc' every time any python file in tests/ or src/
is modified.

Or, as is more common in my zsh history:

```zsh
# Watch python files in all subdirectories and run the tests when they change
ls **/*.py | watchfiles make test
```

Running all the tests takes a long time though.  If I'm working on one module,
I only want to see the output for that module's tests.

```bash
ls ~/my/module.py | watchfiles nosetests tests/unit/test_my_module.py
```

How about something different?

```bash
# Copy file to remote server every time I modify it locally
ls file_to_sync | watchfiles scp file_to_sync server:~
```

Or for those pesky config files:

```bash
# Reload service when its config file is modified
ls path/to/config | watchfiles service appropriate-service reload
```

Execute the script you are working on as you go:
```bash
ls myscript.sh | watchfiles ./myscript
```
