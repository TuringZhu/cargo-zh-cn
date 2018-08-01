## 构建缓存

> [guide/build-cache.md][src]
>
> [commit 72f20b54e5d2391c5dd207cde6cc4b417eb88dd3][commit]

在单一工作区间中的所有包上，Cargo 共享构建制品。现在，在不同的工作区间上，Cargo 并不共享构建结果，但相似结果可以使用第三方工具 [sccache] 实现。

为设置 `sccache` ，使用 `cargo install sccache` 安装 `sccache` 然后在执行 Cargo 之前设置环境变量 `RUSTC_WRAPPER` 。如果使用 bash ，可以将 `export RUSTC_WRAPPER=sccache` 加到 `.bashrc` 中去。参考 sccache 文档以获取更多详情。

[sccache]: https://github.com/mozilla/sccache
[src]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/build-cache.md
[commit]: https://github.com/rust-lang/cargo/commit/72f20b54e5d2391c5dd207cde6cc4b417eb88dd3

