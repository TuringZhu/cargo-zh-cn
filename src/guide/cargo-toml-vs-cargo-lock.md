## Cargo.toml 和 Cargo.lock

> [guide/cargo-toml-vs-cargo-lock.md][src]
>
> [commit bc489e255d6a7cee5531da4992512a9e281000bb][commit]

[src]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/cargo-toml-vs-cargo-lock.md
[commit]: https://github.com/rust-lang/cargo/commit/bc489e255d6a7cee5531da4992512a9e281000bb

`Cargo.toml` 和 `Cargo.lock` 用作两个不同的目的。在讨论它们之前，先看下概要：

* `Cargo.toml` 在广义上描述依赖，并且是由用户编写。
* `Cargo.lock` 包含依赖的精确信息。其由 Cargo 维护且不应该手动编辑。

如果你正在编写一个其他项目所依赖的库，那么请把 `Cargo.lock` 加入到 `.gitignore` 中。如果正在编译一个类似命令行工具的可执行文件或应用，则将 `Cargo.lock` 加到 `git` 里面。如果仍对这样做的目的有所疑惑，则请参考[常见问题中的"为什么二进制的版本控制中有 `Cargo.lock` 而库却没有？](faq.html#why-do-binaries-have-cargolock-in-version-control-but-not-libraries) 。

再深入一点。

`Cargo.toml` 是 **manifest** 文件，在该文件中可以指定与项目有关的一组不同的元数据。例如，可以说我们依赖另一个项目：

```toml
[package]
name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]

[dependencies]
rand = { git = "https://github.com/rust-lang-nursery/rand.git" }
```

该项目只有一个依赖：`rand` 库。这时已经说过我们依赖于 GitHub 上的特定 Git 仓库。由于尚未指定任何其他信息，Cargo 认为我们打算使用 `master` 分支的最新提交来构建项目。

听起来不错？但是，这有个问题：如果你今天构建项目，然后发给我一份拷贝，随后我在明天构建项目，可能会发生些不好的事情。在这期间 `rand` 上可能会有更多提交，然后我的构建可能包含新的提交，但你的构建却没有。因此，我们得到了不同的构建。由于我们需要的是可重复的构建，这样并不好。

可以在 `Cargo.toml` 文件中加上 `rev` 来修复这个问题：

```toml
[dependencies]
rand = { git = "https://github.com/rust-lang-nursery/rand.git", rev = "9f35b8e" }
```

这时我们俩的构建就相同了。但有个很大的缺陷：每次想要更新库时，我们需要考虑 SHA-1 的值。这既无聊而且容易出错。

在 `Cargo.lock` 上，由于它的存在，我们无需手动追踪确切的修改：Cargo 都帮我们做了，现在 manifest 看起来像这样：

```toml
[package]
name = "hello_world"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]

[dependencies]
rand = { git = "https://github.com/rust-lang-nursery/rand.git" }
```

当第一次构建时，Cargo 将会获取最新提交然后将这些信息输出到 `Cargo.lock` 中去，这个文件看起来像这样：

```toml
[[package]]
name = "hello_world"
version = "0.1.0"
dependencies = [
 "rand 0.1.0 (git+https://github.com/rust-lang-nursery/rand.git#9f35b8e439eeedd60b9414c58f389bdc6a3284f9)",
]

[[package]]
name = "rand"
version = "0.1.0"
source = "git+https://github.com/rust-lang-nursery/rand.git#9f35b8e439eeedd60b9414c58f389bdc6a3284f9"
```

该文件中包含更多信息，包括用于构建的精确修改。当对项目做些修改时，其会使用相同的 SHA，即使在 `Cargo.toml` 中不指定它。

当准备创建库的新版本时，Cargo 会重新计算依赖然后更新：

```console
$ cargo update           # updates all dependencies
$ cargo update -p rand   # updates just “rand”
```

这会将新的版本信息输出到 `Cargo.lock` 中去。注意 `cargo update` 的参数实际上是[包 ID 格式](reference/pkgid-spec.html)，而 `rand` 则只是个规范缩写。
