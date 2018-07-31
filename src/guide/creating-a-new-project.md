## 新建项目

> [guide/creating-a-new-project.md][creating-a-new-project]
>
> [commit 9cb10e68a2f225b5e993043f13da98568a41c50a][commit]

[creating-a-new-project]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/creating-a-new-project.md
[commit]: https://github.com/rust-lang/cargo/commit/9cb10e68a2f225b5e993043f13da98568a41c50a

使用 `cargo new` 命令新建项目：

```console
$ cargo new hello_world --bin
```

使用 `--bin` 是因为创建的是二进制程序：如果要创建库，则使用 `--lib` 参数。这也默认初始化了一个新的 `git` 仓库。如果并不需要这样做，请使用 `--vcs none` 参数。 

看下 Cargo 生成了什么：

```console
$ cd hello_world
$ tree .
.
├── Cargo.toml
└── src
    └── main.rs

1 directory, 2 files
```

仔细看看 `Cargo.toml` ：

```toml
[package]
name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
```

这被称为 manifest ，其包括了 Cargo 编译项目的所有元数据。

这是 `src/main.rs` 的内容：

```rust
fn main() {
    println!("Hello, world!");
}
```

Cargo 生成了一个 “hello world”，编译：

```console
$ cargo build
   Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
```

然后运行：

```console
$ ./target/debug/hello_world
Hello, world!
```

也可以用 cargo run 命令编译并运行，都在一个步骤之内（如何自上次编译之后尚未做任何修改，则会看到 `Compiling` ）：

```console
$ cargo run
   Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
     Running `target/debug/hello_world`
Hello, world!
```

现在会留意到一个新文件：`Cargo.lock`。该文件包含了依赖信息。因为尚未有任何依赖，它并是太有趣。

一旦准备发布，可以使用打开优化开关的 `cargo build --release` 命令编译文件。

```console
$ cargo build --release
   Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
```

`cargo build --release` 将二进制文件放在 `target/release` 目录而不是 `target/debug` 目录。

以 debug 模式编译是开发的默认模式 -- 编译时间更短，因为编译器无需优化，但程序运行会稍慢。Release 模式编译耗时较长，但程序运行更快。
