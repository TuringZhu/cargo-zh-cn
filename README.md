# The Cargo Book Simplified Chinese

[![Build Status](https://travis-ci.org/Turing-Chu/cargo-zh-cn.svg?branch=master)](https://travis-ci.org/Turing-Chu/cargo-zh-cn)


### Require

This book is build by [mdbook]。You can install it by：

[mdBook]: https://github.com/azerupi/mdBook

```console
$ cargo install mdbook
```

### Build

build the book:

```console
$ mdbook build
```

This command will output files to `boot` directory. Please checkout it in Broswer.

_Firefox:_
```console
$ firefox book/index.html                       # Linux
$ open -a "Firefox" book/index.html             # OS X
$ Start-Process "firefox.exe" .\book\index.html # Windows (PowerShell)
$ start firefox.exe .\book\index.html           # Windows (Cmd)
```

_Chrome:_
```console
$ google-chrome book/index.html                 # Linux
$ open -a "Google Chrome" book/index.html       # OS X
$ Start-Process "chrome.exe" .\book\index.html  # Windows (PowerShell)
$ start chrome.exe .\book\index.html            # Windows (Cmd)
```


## Contribute

鉴于本书仍处于编写状态，我们非常乐意为您提供帮助！请随意提出任何问题，并在 PR 中发送您想要修改或更新的内容。如果您的更改较大，请先开一个 issue ，这样我们便可以确保这是我们可以接受的事情，
