#gitprint-download

Thanks to @adamburmister for [gitprint](https://github.com/adamburmister/gitprint.com)
which is what this script uses.

gitprint-download is a bash script that will use gitprint to convert a chosen
markdown file, and then download that converted pdf document to the current
working directory.

##Usage

gitprint expects 1 argument. That argument can either be the github URL of the
file you wish to convert and download, or the name of the file that is local on
your machine (currently, this file must be in the current working directory).

This script also cannot download a converted file from a private repo. This is
because gitprint does not support this at this time.

###Examples

NOTE: do not try these, they don't work because no such url or file exist


```bash
$ ./gitprint https://github.com/username/repo/blob/branch/filename.md

$ ls
filename.pdf
```

NOTE: at this time, if you just use the filename as below, the script assumes
you want it from the master branch. There is not currently a way to specify
otherwise unless you give the full URL as above.

```bash
$ ls
filename.md
$ ./gitprint filename.md

$ ls
filename.md  filename.pdf
```
