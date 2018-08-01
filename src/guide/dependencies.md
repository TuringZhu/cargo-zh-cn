## 依赖

> [guide/dependencies.md][dependencies]
>
> [commit 55b72dd197910afed517fb15b87b97748a57296a][commit]

[dependencies]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/dependencies.md
[commit]: https://github.com/rust-lang/cargo/commit/55b72dd197910afed517fb15b87b97748a57296a

[crates.io] 是 Rust 社区的包注册中心，其可用于发现和下载包的网址。`cargo` 将它用作发现所需包的默认配置。

将在 [crates.io] 登记到依赖库加到 `Cargo.toml` 文件中。

[crates.io]: https://crates.io/

### 添加依赖

如果 `Cargo.toml` 没有 `[dependencies]` 部分，那么加上它，然后列举包名以及你所使用的版本。该例子添加了 `time` 包的依赖：

```toml
[dependencies]
time = "0.1.12"
```

版本名为 [semver] 的版本条件。[指定依赖](reference/specifying-dependencies.html) 部分有更多选项信息。

[semver]: https://github.com/steveklabnik/semver#requirements

如果也想添加 `regex` 包的依赖，则无需为每个所列包加上 `[dependencies]` 。下面是依赖 `time` 包和 `regex` 包的整个 `Cargo.toml` 文件的内容：

```toml
[package]
name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]

[dependencies]
time = "0.1.12"
regex = "0.1.41"
```

重新运行 `cargo build`，Cargo 会拉取新的依赖以及依赖包的依赖，编译然后更新 `Cargo.lock` ：

```console
$ cargo build
      Updating registry `https://github.com/rust-lang/crates.io-index`
   Downloading memchr v0.1.5
   Downloading libc v0.1.10
   Downloading regex-syntax v0.2.1
   Downloading memchr v0.1.5
   Downloading aho-corasick v0.3.0
   Downloading regex v0.1.41
     Compiling memchr v0.1.5
     Compiling libc v0.1.10
     Compiling regex-syntax v0.2.1
     Compiling memchr v0.1.5
     Compiling aho-corasick v0.3.0
     Compiling regex v0.1.41
     Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
```

`Cargo.lock` 包含所有所依赖的修订版的确切信息。

如果 `regex` 更新了，构建时仍使用同一个校订除非选择 `cargo update` 。

现在可以通过在 `main.rs` 中用 `extern crate` 来使用 `regex` 库了。

```rust
extern crate regex;

use regex::Regex;

fn main() {
    let re = Regex::new(r"^\d{4}-\d{2}-\d{2}$").unwrap();
    println!("Did our date match? {}", re.is_match("2014-01-01"));
}
```

执行时将会输出：

```console
$ cargo run
   Running `target/hello_world`
Did our date match? true
```
