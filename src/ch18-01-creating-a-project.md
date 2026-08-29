/*
## Creating a Citrus Project
*/

## Citrusプロジェクトを作成する

<!--
### Project Structure
-->

### プロジェクト構造

<!--
A Lime project is a directory with a `citrus.toml` manifest:
-->

Limeプロジェクトは`citrus.toml`マニフェストを持つディレクトリです:

```toml
[package]
name = "my_app"
version = "0.1.0"

[files]
main = "main.lime"

[dependencies]
string = "v0.1.0"
collections = "v0.1.0"
```

<!--
### Creating a New Project
-->

### 新しいプロジェクトの作成

```console
$ citrus new my_app
```

<!--
### Building a Project
-->

### プロジェクトのビルド

```console
$ citrus build
$ citrus build --release
```

<!--
### Running a Project
-->

### プロジェクトの実行

```console
$ citrus run
$ citrus run --release
```

<!--
### Running with Arguments
-->

### 引数付きで実行

<!--
You can forward arguments to the executable:
-->

実行ファイルに引数を渡すことができます:

```console
$ citrus run -- arg1 arg2
```

<!--
### Testing
-->

### テスト

<!--
Run tests in your project:
-->

プロジェクトのテストを実行します:

```console
$ citrus test
```

<!--
### Managing Dependencies
-->

### 依存関係の管理

<!--
Add or remove dependencies:
-->

依存関係を追加・削除します:

```console
$ citrus add string
$ citrus remove string
```

<!--
Install and update dependencies from the bundled stdlib:
-->

バンドルされた標準ライブラリから依存関係をインストール・更新します:

```console
$ citrus install
$ citrus update
```

<!--
### Single-File Programs
-->

### シングルファイルプログラム

<!--
You can also run single `.lime` files directly:
-->

シングルの`.lime`ファイルも直接実行できます:

```console
$ lime run hello.lime
$ lime hello.lime
```
