## 项目布局

> [guide/project-layout.md][src]
>
> [commit bc489e255d6a7cee5531da4992512a9e281000bb][commit]

[src]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/project-layout.md
[commit]: https://github.com/rust-lang/cargo/commit/bc489e255d6a7cee5531da4992512a9e281000bb

Cargo 使用文件放置惯例，使其便于投身于新的 Cargo 项目：

```
.
├── Cargo.lock
├── Cargo.toml
├── benches
│   └── large-input.rs
├── examples
│   └── simple.rs
├── src
│   ├── bin
│   │   └── another_executable.rs
│   ├── lib.rs
│   └── main.rs
└── tests
    └── some-integration-tests.rs
```

* `Cargo.toml` 和 `Cargo.lock` 存储在项目根目录下（*包目录*）。
* 源代码位于 `src` 目录。
* 默认库文件为 `src/lib.rs` 。
* 默认可执行文件为 `src/main.rs` 。
* 其他可执行文件可以放于 `src/bin/*.rs` 。
* 集成测试位于 `tests` 目录（单元测试放在每个文件中。）
* 示例文件位于 `examples` 目录。
* Benchmark 位于 `benches` 目录。

这些在 [manifest 描述](reference/manifest.html#the-project-layout) 有更详细的解释。
