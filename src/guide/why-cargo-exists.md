## Cargo 存在的原因

> [guide/why-cargo-exists.md][why-cargo-exists]
>
> [commit 1271bb4de0c0e0a085be239c2418af9c673ffc87][commit]

[why-cargo-exists]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/why-cargo-exists.md
[commit]: https://github.com/rust-lang/cargo/commit/1271bb4de0c0e0a085be239c2418af9c673ffc87

Cargo 是一个可以让 Rust 项目声明其各种依赖并保证可一直重复构建的工具。

为了达到这个目标，Cargo 做了四件事：

* 引入两个包含项目各种信息的元数据文件。
* 获取并构建项目依赖。
* 调用 `rustc` 或其他构建工具并使用正确的构建参数来构建项目。
* 引入简便性以便在 Rust 项目上工作更加容易。
