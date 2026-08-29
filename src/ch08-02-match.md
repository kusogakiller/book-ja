/*
## The `match` Control Flow Construct
*/

## `match`制御フロー構造

<!--
`match` allows you to compare a value against a series of patterns and then
execute code based on which pattern matches. It must be exhaustive.
-->

`match`は値を一連のパターンと比較し、どのパターンがマッチするかに応じて
コードを実行します。網羅的である必要があります。

<!--
### Basic Usage
-->

### 基本的な使い方

```lime
match Some(5):
    Some(v):
        println(v)
    None:
        println("none")
```

<!--
### Patterns
-->

### パターン

<!--
The patterns include:
-->

パターンには以下が含まれます:

- `Some(v)` / `None` — `Option`バリアント
- `Variant(a, b)` — 構造体ライクなstate/enumバリアント
- `catch:` — 捕捉すべて（ワイルドカードとして機能）
- `try (a, b)` — タプルパターン

<!--
### Catch-all Pattern
-->

### 捕捉パターン

<!--
The `catch:` pattern matches anything, similar to `_` in other languages.
-->

`catch:`パターンは他の言語の`_`と同様に何にでもマッチします:

```lime
let d = North
match d:
    North:
        println("north")
    catch:
        println("other")
```

<!--
### Exhaustive Matching
-->

### 網羅的マッチング

<!--
`match` must be exhaustive — all variants must be covered. There is no `else`
arm.
-->

`match`は網羅的である必要があります — すべてのバリアントをカバーする必要があります。
`else`分岐はありません。

```lime
// This would cause a compile error if State has more variants:
match d:
    North:
        println("north")
    catch:
        println("other")
```
