/*
## Defining Modules to Control Scope
*/

## モジュールを定義してスコープを制御する

<!--
Lime uses a simple module system. Each file is a module, and you can import
modules using the `import` keyword.
-->

Limeはシンプルなモジュールシステムを使用します。各ファイルはモジュールであり、
`import`キーワードを使用してモジュールをインポートできます。

<!--
### Importing Modules
-->

### モジュールのインポート

```lime
import std.string

fn main():
    println(std.string.trim("  hello  "))
    return
```

<!--
### Module Paths
-->

### モジュールパス

<!--
Modules are accessed using their full path:
-->

モジュールにはフルパスでアクセスします:

```lime
import std.string

fn main():
    println(std.string.to_upper("abc"))
    println(std.string.contains("lime", "im"))
    return
```

<!--
### Standard Library Modules
-->

### 標準ライブラリモジュール

<!--
The standard library modules are accessed via the `std` namespace:
-->

標準ライブラリモジュールには`std`名前空間を通じてアクセスします:

```lime
import std.string
import std.math
import std.fs
import std.time
```
