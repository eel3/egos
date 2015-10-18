egos; embed golang script in shell script
=========================================

Command line tool to embed golang script in shell script.

License
-------

zlib License.

Target environments
-------------------

Windows, Linux, Mac OS X.

egos is written in Go 1.5.1, and so probably works fine on other OS.

Set up
------

1. Install [Go](https://golang.org/ "Official website") 1.5.1 or later.
2. Compile egos.go (`go build egos.go`).
3. Put egos in a directory registered in PATH.

Usage
-----

Please check help message `egos -h`

Example
-------

```sh
egos -i '"fmt"' 'fmt.Println("hello, world")'
#=> "hello, world\n"

egos -i '"fmt";"os"' '
for _, s := range os.Args {
    fmt.Println(s)
}' a BB  'c  c'
#=> "a\nBB\nc  c\n"

egos -i 'f "fmt"' -n 'f.Println(line)' <<'END'
foo
bar
baz
END
#=> "foo\nbar\nbaz\n"

egos -i 'f "fmt"' -p 'f.Println(line)' <<'END'
foo
bar
baz
END
#=> "foo\nfoo\nbar\nbar\nbaz\nbaz\n"
```
