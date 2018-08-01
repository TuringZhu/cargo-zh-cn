## 初次使用 Cargo

> [getting-started/first-steps.md][first-steps]
>
> [commit 0f835654737e919d125ca17f37f520a34c84bc3e][commit]

[first-steps]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/getting-started/first-steps.md
[commit]: https://github.com/rust-lang/cargo/commit/0f835654737e919d125ca17f37f520a34c84bc3e

使用 `cargo new` 来新建一个项目：

```console
$ cargo new hello_world --bin
```

由于我们创建的是二进制项目，所以使用了 `--bin` 参数：如果要创建库项目，则需要 `--lib` 参数。

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

这便是刚开始所需要的。首先，来看看 `Cargo.toml` 文件的内容：

```toml
[package]
name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
```

这被称为 **manifest** ，其包括了 Cargo 编译项目的所有元数据。

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

也可以用 `cargo run` 命令编译并运行，都在一个步骤之内：

```console
$ cargo run
     Fresh hello_world v0.1.0 (file:///path/to/project/hello_world)
   Running `target/hello_world`
Hello, world!
```

### 深入

关于使用 Cargo 的更多细节，查阅 [Cargo 指引](guide/index.html)
