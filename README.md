Introduction
====

csvmaster is a tool for working with CSV files on the command line. Why would you want that when you have `cut` and `awk`? Because `cut` and `awk` don't have any idea what to do with quoted fields. Because `sed` and `awk` can't distinguish between a field separator char that actually separates fields, and one that's inside a field's value. Because if you change the delimeter with those tools, they don't know how to quote fields containing the new delimiter.

csvmaster fixes all of that by using an actual CSV parsing engine for reading, writing, and field splitting.

Usage
====

To print out select fields:
`csvm --fields=0,1,2 test.csv`

To print them out with a different separator:
`csvm --fields=0,1,2 --out='\t' test.csv`

To use an input separator that is not a comma
`csvm --file=test.csv --in='\t' --out=','`

Perhaps you want to actually use `sed`/`awk` to parse your data. This command will let you correctly separate your fields, then write out an unquoted CSV with a separator you can more safely parse with stardard command-line tools.
`cat test.csv | csvm --out='|' --no-rfc`

Some lines may be commented out. You may ignore these lines:
`cat test.csv | csvm --out='|' --comment-char='#'`


Short flags
-----------

csvm also accepts short flags:

- -f = filename
- -F = field numbers
- -i = input separator
- -o = output separator


Download
====

v1.1 for:

- [Linux x86](https://github.com/spiffytech/csvmaster/releases/download/v1.1/csvm_linux_x86)
- [Linux x64](https://github.com/spiffytech/csvmaster/releases/download/v1.1/csvm_linux_x64)
- [Source tarball](https://github.com/spiffytech/csvmaster/archive/v1.1.tar.gz)


Building
====

[Install Go](http://golang.org/doc/install#install)

`go build -o csvm csvmaster.go`
