## 安装

> [getting-started/installation.md][installation]
>
> [commit 3e4d1558ab63605d15d6d143b0b5f89ea579a8b8][commit]

[installation]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/getting-started/installation.md
[commit]: https://github.com/rust-lang/cargo/commit/3e4d1558ab63605d15d6d143b0b5f89ea579a8b8

### 安装 Rust 和 Cargo

获取 Cargo 的最简易方式是使用 `rustup` 来安装当前稳定版 [Rust] 。

在 Linux 和 macOS 系统上，按如下方式安装：

```console
$ curl -sSf https://static.rust-lang.org/rustup.sh | sh
```

这样会下载一个脚本，然后开始安装。如果一切顺利，会看到这样的输出：

```console
Rust is installed now. Great! 
```

在 Windows 上，下载并运行 [rustup-init.exe] 。它将在一个控制台中开始安装然后成功之后显示上面的信息。

之后，可以用 `rustup` 命令来安装 `beta` 版或 `nightly` 版的 Rust 与 Cargo 。

关于其他安装选项与信息，访问 Rust 网站的[安装][install-rust]页面。

### 源码编译并安装 Cargo

另外，也可以[源码编译 Cargo][compiling-from-source] 。

[rust]: https://www.rust-lang.org/
[rustup-init.exe]: https://win.rustup.rs/
[install-rust]: https://www.rust-lang.org/install.html
[compiling-from-source]: https://github.com/rust-lang/cargo#compiling-from-source
