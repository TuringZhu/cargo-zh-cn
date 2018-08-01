## 包 ID 格式

> [reference/pkgid-spec.md][pkgid-spec]
>
> [commit 1271bb4de0c0e0a085be239c2418af9c673ffc87][commit]

[pkgid-spec]: https://github.com/rust-lang/cargo/blob/master/src/doc/src/reference/pkgid-spec.md
[commit]: https://github.com/rust-lang/cargo/commit/1271bb4de0c0e0a085be239c2418af9c673ffc87

### 包 ID 格式

在像更新、清理、构建等针对依赖图的各种操作中，Cargo 的子命令通常需要指定具体的包。为了解决这个问题，Cargo 提供了包 ID 格式。格式是一个字符串，在包的结构图中用于指定特定的包。

#### 格式语法

包 Id 格式的正式语法为：

```notrust
pkgid := pkgname
       | [ proto "://" ] hostname-and-path [ "#" ( pkgname | semver ) ]
pkgname := name [ ":" semver ]

proto := "http" | "git" | ...
```

此处，大括号指明其内容是可选的。

#### 示例格式

这些都可以作为在 `crates.io` 上注册的包 `foo` 的 `1.2.3` 版本。

| pkgid                        | name  | version | url                    |
|:-----------------------------|:-----:|:-------:|:----------------------:|
| `foo`                        | `foo` | `*`     | `*`                    |
| `foo:1.2.3`                  | `foo` | `1.2.3` | `*`                    |
| `crates.io/foo`              | `foo` | `*`     | `*://crates.io/foo`    |
| `crates.io/foo#1.2.3`        | `foo` | `1.2.3` | `*://crates.io/foo`    |
| `crates.io/bar#foo:1.2.3`    | `foo` | `1.2.3` | `*://crates.io/bar`    |
| `http://crates.io/foo#1.2.3` | `foo` | `1.2.3` | `http://crates.io/foo` |

####  简短格式

这样做的目的是为了在依赖图中引用包时保证简洁且详尽的语法。模凌两可的引用可能指向一个或多个包。如果同一格式指向了多个包，大多数命令都会产生错误。
