## 测试

> [guide/tests.md][test]
>
> [commit bc489e255d6a7cee5531da4992512a9e281000bb][commit]

[test]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/tests.md
[commit]: https://github.com/rust-lang/cargo/commit/bc489e255d6a7cee5531da4992512a9e281000bb

Cargo 可以使用 `cargo test` 命令来运行测试。Cargo 查找测试然后在两个地方执行测试：`src` 下的每一个文件中以及 `tests/` 目录下的任何测试。
在 `src` 文件中的测试应为单元测试，而在 `tests/` 下的测试则应为集成测试。因此，需要导入项目 crate 到 `tests` 里的文件中。

Here's an example of running `cargo test` in our project, which currently has
no tests:

```console
$ cargo test
   Compiling rand v0.1.0 (https://github.com/rust-lang-nursery/rand.git#9f35b8e)
   Compiling hello_world v0.1.0 (file:///path/to/project/hello_world)
     Running target/test/hello_world-9c2b65bbb79eabce

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

如果项目有测试，需要留意通过测试的数量。

也可以传递一个过滤器来运行指定的测试：

```console
$ cargo test foo
```

这会运行所有测试名包含 `foo` 的测试。

`cargo test` 也执行额外的检查。例如，其会对包含其中任何例子进行编译，并且在文档中测试该例子。请在 Rust 文档中查阅[测试指引][testing]以获取更多详情。

[testing]: https://doc.rust-lang.org/book/testing.html
