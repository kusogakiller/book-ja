/*
## How to Write Tests
*/

## テストの記述法

<!--
Lime tests are written using standard Lime code. The `lime check` command
verifies that code type-checks correctly.
-->

Limeのテストは標準的なLimeコードで書かれます。`lime check`コマンドは
コードが正しく型チェックされることを確認します。

<!--
### Type Checking
-->

### 型チェック

<!--
The simplest form of testing is type checking:
-->

最もシンプルなテストは型チェックです:

```console
$ lime check hello.lime
ok: hello.lime type-checks cleanly
```

<!--
### Integration Tests
-->

### 統合テスト

<!--
Lime uses Rust-based integration tests. The test suite can be run with:
-->

LimeはRustベースの統合テストを使用します。テストスイートは以下で実行できます:

```console
$ cargo test --lib
$ cargo test --test integration
$ cargo test
```

<!--
### Diagnostic Tests
-->

### 診断テスト

<!--
Lime has diagnostic tests that verify error messages are correct:
-->

Limeにはエラーメッセージが正しいことを確認する診断テストがあります:

```console
$ cargo test --test diagnostic_tests
```
