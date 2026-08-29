/*
## Controlling How Tests Are Run
*/

## テストの実行

<!--
Lime provides several ways to run tests and verify code.
-->

Limeはコードを実行・確認するいくつかの方法を提供します。

<!--
### Unit Tests
-->

### ユニットテスト

```console
$ cargo test --lib
```

<!--
### Integration Tests
-->

### 統合テスト

```console
$ cargo test --test integration
```

<!--
### All Tests
-->

### すべてのテスト

```console
$ cargo test
```

<!--
### Type Check Only
-->

### 型チェックのみ

```console
$ lime check hello.lime
```
