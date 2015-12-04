#gitprint-download

Thanks to [@adamburmister](https://github.com/adamburmister) for [gitprint](https://github.com/adamburmister/gitprint.com)
which is what this script uses.

gitprint-download is a bash script that will use gitprint to convert a chosen
markdown file, and then download that converted pdf document to the current
working directory.

##Usage

gitprint expects 1 argument, but there is an optional second:
  1. Can either be the github URL of the file you wish to convert and download,
or the name of the file that is local on your machine (currently, this file must
be in the current working directory).
  2. Can be a specified branch. For example, if you want a file from a branch
that you called "branch2", then specify "branch2" as the second argument
(This only works for when you specify a filename, not a URL. This is because the
branch name is already in the URL).

If a second argument is not provided when using the filename and no URL, then it
defaults to whatever branch you currently have checked out.

This script also cannot download a converted file from a private repo. This is
because gitprint does not support this at this time.

###Examples

NOTE: do not try these, they don't work because no such url or file exist


```bash
$ ./gitprint https://github.com/username/repo/blob/branch/filename.md

$ ls
filename.pdf
```

NOTE: Currently, the file being asked for must be in the root folder of the
repo. As of now, if it is nested in subdirectories, you must use the above
method.

NOTE: This does not use the current version on your local system. It uses the
current version that has been pushed to github

```bash
$ ls
filename.md
$ ./gitprint filename.md

$ ls
filename.md  filename.pdf
```

Below, I have specified to use the version in the issue#1 branch.

```bash
$ ls
filename.md
$ ./gitprint filename.md issue#1

$ ls
filename.md  filename.pdf
```
