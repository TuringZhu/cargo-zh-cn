## 持续集成（CI）

> [guide/continuous-integration.md][ci]
>
> [commit f84ec4fc5523472806669c9ae2afa763ee3837ce][commit]

[ci]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/guide/continuous-integration.md
[commit]: https://github.com/rust-lang/cargo/commit/f84ec4fc5523472806669c9ae2afa763ee3837ce

### Travis CI

下面是可以在 Travis CI 上测试项目的 `.travis.yml` 示例文件：

```yaml
language: rust
rust:
  - stable
  - beta
  - nightly
matrix:
  allow_failures:
    - rust: nightly
```

这会测试三个发布通道，但在 nightly 中的任何断点并不会造成整个构建的失败。请查阅 [Travis CI Rust 文档](https://docs.travis-ci.com/user/languages/rust/)以获取更多信息。

### GitLab CI

下面是可以在 GitLab CI 上测试项目的 `.gitlab-ci.yml` 示例文件：

```yaml
stages:
  - build

rust-latest:
  stage: build
  image: rust:latest
  script:
    - cargo build --verbose
    - cargo test --verbose

rust-nightly:
  stage: build
  image: rustlang/rust:nightly
  script:
    - cargo build --verbose
    - cargo test --verbose
  allow_failure: true
```

这会在 stable 通道和 nightly 通道上测试，但在 nightly 上的任何断点并不会造整个构建的失败。查阅 [GitLab CI](https://docs.gitlab.com/ce/ci/yaml/README.html) 以获取更多信息。
