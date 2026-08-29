/*
## Reading a File
*/

## ファイルを読み込む

<!--
Lime provides file I/O through the `fs` package and built-in functions.
-->

Limeは`fs`パッケージと組み込み関数を通じてファイルI/Oを提供します。

<!--
### Reading Files
-->

### ファイルの読み込み

```lime
fn main():
    let content = read_file("hello.txt")
    println(content)
    return
```

<!--
### Writing Files
-->

### ファイルの書き込み

```lime
fn main():
    write_file("output.txt", "hello, world")
    let loaded = read_file("output.txt")
    println(loaded)
    return
```

<!--
### File System Module
-->

### ファイルシステムモジュール

<!--
The `fs` package provides additional file operations:
-->

`fs`パッケージは追加のファイル操作を提供します:

```lime
fn main():
    write_file("audit_report.txt", "TASKS=2\nDONE=1\n")
    let loaded = read_file("audit_report.txt")
    println(loaded == "TASKS=2\nDONE=1\n")
    println(loaded.len())
    return
```
