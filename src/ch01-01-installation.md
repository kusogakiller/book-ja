/*
## Installation
*/

## インストール

<!--
The first step is to install Lime. The Lime compiler is a Rust program that you
build from source using Cargo.
-->

最初の手順は、Limeをインストールすることです。Limeコンパイラは、Cargoを使用してソースからビルドするRustプログラムです。

<!--
### Building from Source
-->

### ソースからビルドする

<!--
To build the Lime compiler, you'll need Rust and Cargo installed. Then clone
the Lime repository and build:
-->

Limeコンパイラをビルドするには、RustとCargoがインストールされている必要があります。
Limeリポジトリをクローンしてビルドしてください:

```console
$ git clone https://github.com/kusogakiller/lime.git
$ cd lime
$ cargo build --release
```

<!--
This produces a `lime` executable (on Windows, `target\release\lime.exe`).
-->

これで`lime`実行ファイルが生成されます（Windowsでは`target\release\lime.exe`）。

<!--
### Verifying the Installation
-->

### インストールを確認する

<!--
To check whether you have Lime installed correctly, run:
-->

Limeが正常にインストールされているか確かめるには、以下を実行してください:

```console
$ lime --help
```

<!--
### The Command Line Interface
-->

### コマンドラインインターフェース

<!--
Lime provides the following commands:
-->

Limeは以下のコマンドを提供します:

```
lime build <path> [--emit-ll] [--emit-object] [--release] [--verbose|-v]  Build to binary
lime run   <path> [--emit-ll] [--verbose|-v]                              Build and execute
lime check <path> [--verbose|-v]                                          Type-check only
lime fmt   <file.lime> [--write]                                          Format source
lime <path> [--emit-ll] [--verbose|-v]                                    Shorthand for `run`
```

<!--
`--verbose` / `-v` prints compiler diagnostics to stderr.
-->

`--verbose` / `-v`はコンパイラの診断情報をstderrに出力します。

<!--
### Charger (FFI Helper)
-->

### Charger（FFIヘルパー）

<!--
Lime includes `lime charger`, a tool for building and managing C/C++ library
bindings for FFI.
-->

Limeには`lime charger`が含まれています。これはFFI用のC/C++ライブラリバインディングを
ビルド・管理するツールです。

```
lime charger install <source>       Build and install a C/C++ library
lime charger list                   List installed libraries
lime charger verify-abi <lib>       Verify ABI signature
lime charger verify-semantics <lib> Verify semantic metadata
lime charger verify-contract <lib>  Verify ABI contract
```

<!--
For project builds there is also the `citrus` CLI (a wrapper around lime):
-->

プロジェクトビルドには`citrus`CLI（limeのラッパー）もあります:

```
citrus new <name>        Create a new project
citrus build [--release] Build a project (citrus.toml in the current directory)
citrus run  [--release]  Build and run a project
```

<!--
### Platform Requirements
-->

### プラットフォーム要件

<!--
The interpreter does not require an LLVM installation. Native compilation
(`--emit-object`) requires `clang`, `llvm-as`, and `lld-link` from LLVM 22
on your `PATH` (or the `LIME_LLVM_PREFIX` / `LLVM_SYS_221_PREFIX` environment
variable pointing at the LLVM install directory).
-->

インタプリタにはLLVMのインストールは必要ありません。ネイティブコンパイル
（`--emit-object`）には、LLVM 22の`clang`、`llvm-as`、`lld-link`が`PATH`に
必要です（またはLLVMインストールディレクトリを指す`LIME_LLVM_PREFIX` / `LLVM_SYS_221_PREFIX`
環境変数）。

<!--
> Note: Source files must use **LF line endings** and must be **ASCII**.
> Non-ASCII bytes (for example in comments) fail to tokenize.
-->

> 注釈: ソースファイルは**LF行末**を使用し、**ASCII**である必要があります。
> ASCII以外のバイト（コメント内の例など）はトークン化に失敗します。
