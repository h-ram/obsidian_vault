A **dashed file name** is simply a file whose name **starts with a dash (`-`)**. In Linux and Unix-like systems, this is problematic because most commands interpret anything that starts with a dash as a **command-line option**, not a file name.
```bash
$ > ls -l
-rw-r----- 1 user group 33 Sep 19 07:08 -
-rw-r----- 1 user group 33 Sep 19 07:08 -myfile
-rw-r----- 1 user group 33 Sep 19 07:08 --randomFile
```

Any attempt to treat these files normaly will cause an error, since the shell will think you're entering an option instead of the file name.
```bash
$ > cat -myfile
cat: invalid option -- 'h'
```
You can easily overcome is naming problem just by specifiy the directory `./`
```bash
$ > cat ./-myfile
It worked! :)
```