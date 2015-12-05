#gitprint-download

Thanks to [@adamburmister](https://github.com/adamburmister) for [gitprint](https://github.com/adamburmister/gitprint.com)
which is what this script uses.

Note that gitprint supports the following three markdown file extensions, so
this does as well:
  * md
  * mdown
  * markdown

Nothing else will work.

gitprint-download is a bash script that will use gitprint to convert a chosen
markdown file, and then download that converted pdf document to the current
working directory.

##Usage

gitprint expects 1 mandatory argument which can either be the github URL of the
file you wish to convert and download, or the name and/or path of the file that
is local on your machine.



Full file paths can be used for the filename. You do not need to be in the same
location as the file you are downloading.

This script cannot download a converted file from a private repo. This is
because gitprint does not support this at this time.

NOTE: This does not use the current version on your local system. It uses the
current version that has been pushed to github

###Special URL Characters

Note that the only way to ensure that a URL will work is to copy and paste the
URL directly from a web browser of a public repo. If you edit a URL there is a
possibility that it will not work.

As an example, consider this URL:

```
https://github.com/username/repo/blob/master/filename.md
```

Now lets say that I want to get filename.md from a branch called issue#1. If I
edit the URL directly to get this:

```
https://github.com/username/repo/blob/issue#1/filename.md
```

This would fail (okay, this specific example will work, but only for reasons
that I am going to explain further down). If you were to go to this branch in a
web browser, issue#1 would look like "issue%231". Notice that the "#" is
replaced with a "%23".

The above example will work because I have provided a fix for it in the code. I
will add more exceptions as they are needed and requested, but just keep this in
mind.

Below are the special characters that are supported so far:
  * # = %23


###Examples

####Basic URL Example

```bash
$ ./gitprint https://github.com/username/repo/blob/branch/filename.md

$ ls
filename.pdf
```

####Basic Filename Example

```bash
$ ls
filename.md
$ ./gitprint filename.md

$ ls
filename.md  filename.pdf
```

####Subdirectory Example

Full filepaths also work.

```bash
$ ls
testdir
$ ls testdir
filename.md
$ ./gitprint testdir/filename.md

$ ls
testdir  filename.pdf
$ rm -rf filename.pdf
$ ./gitprint ./testdir/filename.md

$ ls
testdir  filename.pdf
```

###Optional Arguments

####--dest-dir

The default value of this flag is the location of the markdown file you are
converting.

This flag specifies where you would like the converted pdf file to be saved.

example:

```bash
$ ./gitprint filename.md --dest-dir ~/Documents
```

```bash
$ ./gitprint https://github.com/username/repo/blob/branch/filename.md --dest-dir ~/Documents
```

####--branch

NOTE: This option can only be used with a filename, not a URL. If a URL is
provided, this flag will be ignored (github URLs specify the branch to use).

The default value is the branch that is currently checked out.

This flag is used in order to specify a  branch.

If you want a file named "filename.md" to be converted to pdf, but you want the
version from you branch that you called "Branch2"

```bash
$ ./gitprint filename.md --branch Branch2
```



