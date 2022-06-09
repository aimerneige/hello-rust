# Cargo

## 创建项目

```bash
cargo new hello_world
cd hello_world
```

## 运行项目

```bash
cargo run
```

以上指令相当于手动执行如下指令（先编译后执行可执行文件）：

```bash
cargo build
./target/debug/hello_world
```

上面的指令会以 debug 模式编译项目，它有更快的编译速度，但同时运行速度比较慢，如果想要更好的性能，可以以 release 模式编译：

```bash
cargo run --release
```

```bash
cargo build --release
./target/release/hello_world
```

## 检查语法错误

当项目变大之后，即使是使用 debug 模式编译项目也会非常慢，如果我们需要通过编译来检查代码是否存在错误，同时不需要实际运行，可以使用 `cargo check` 来检查代码的正确性：

```bash
cargo check
```

## `Cargo.toml` 和 `Cargo.lock`

`Cargo.toml` 里包含了项目的基本信息和其依赖库，我们需要手动修改它。

`Cargo.lock` 由 `cargo` 工具生成，一般不需要修改。

当项目是一个可执行的程序时，要把 `Cargo.lock` 也上传到 git 仓库里。如果是一个依赖库时，需要把它添加到 `.gitignore` 中。

## package 配置段落

```toml
[package]
name = "hello_world"
version = "0.1.0"
edition = "2021"
```

`name` 字段定义了**项目名称**
`version` 字段定义了**项目版本号**
`edition` 字段定义了**项目使用的 Rust 大版本**

## 定义项目依赖

- 基于 Rust 官方仓库 crates.io，通过版本说明来描述
- 基于项目源代码的 git 仓库地址，通过 URL 来描述
- 基于本地项目的绝对路径或者相对路径，通过类 Unix 模式的路径来描述

这三种形式具体写法如下：

```toml
[dependencies]
rand = "0.3"
hammer = { version = "0.5.0"}
color = { git = "https://github.com/bjz/color-rs" }
geometry = { path = "crates/geometry" }
```
