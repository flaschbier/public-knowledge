# Pushing Your Changes Correctly

When you just

```sh
git add -A
git commit -m "fooling around"
git push origin master
```

you will end up with CI error like so:

```
Obtaining file:///home/runner/work/collatz/collatz
    ERROR: Command errored out with exit status 1:
     command: /opt/hostedtoolcache/Python/3.6.10/x64/bin/python -c 'import sys, setuptools, tokenize; sys.argv[0] = '"'"'/home/runner/work/collatz/collatz/setup.py'"'"'; __file__='"'"'/home/runner/work/collatz/collatz/setup.py'"'"';f=getattr(tokenize, '"'"'open'"'"', open)(__file__);code=f.read().replace('"'"'\r\n'"'"', '"'"'\n'"'"');f.close();exec(compile(code, __file__, '"'"'exec'"'"'))' egg_info
         cwd: /home/runner/work/collatz/collatz/
    Complete output (6 lines):
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/home/runner/work/collatz/collatz/setup.py", line 41
        python_requires  = '>=' + cfg['min_python'],
                      ^
    SyntaxError: invalid syntax
    ----------------------------------------
ERROR: Command errored out with exit status 1: python setup.py egg_info Check the logs for full command output.
##[error]Process completed with exit code 1.
```

