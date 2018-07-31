## 在已有项目上工作

> [guide/working-on-an-existing-project.md][src]
>
> [commit bc489e255d6a7cee5531da4992512a9e281000bb][commit]

[src]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/working-on-an-existing-project.md
[commit]: https://github.com/rust-lang/cargo/commit/bc489e255d6a7cee5531da4992512a9e281000bb

如果下载使用 Cargo 的现有项目，则比较容易上手。

首先获取项目，在该例子中。会用从 GitHub 上克隆的 `rand`： 

```console
$ git clone https://github.com/rust-lang-nursery/rand.git
$ cd rand
```

使用 `cargo build` 编译：

```console
$ cargo build
   Compiling rand v0.1.0 (file:///path/to/project/rand)
```

这将拉取所有依赖，然后和项目一起构建。
