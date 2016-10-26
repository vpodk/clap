# How to compare two folders in command line on Linux and macOS.

If you want to clear up duplicates or find out which folder includes particular files and which does not,
using the `diff` command in the Terminal will help you find out quickly.

It is commonly used to check the distinction between any files using this:

```bash
diff path-to-file-1 path-to-file-2
```

Just by adding `-rq` options you can compare the contents of two folders:

```bash
diff -rq path-to-folder-1 path-to-folder-2
```

The `r` option tells to recursively compare any subdirectories found
and the `q` option to output only whether files differ.

**Note:** The `q` option is not available on [POSIX](https://en.wikipedia.org/wiki/POSIX).

When this command is entered, switching `folder-1` and `folder-2` to the folders you would like to analyze -- the terminal will give a list of dissimilarities between them.

For more information on the full capabilities of `diff`, use `man diff` or read it online at [man7.org](http://man7.org/linux/man-pages/man1/diff.1.html).
