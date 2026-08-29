/*
## Control Flow
*/

## 制御フロー

<!--
Lime provides several control flow constructs: if/elif/else, while, for, and
match.
-->

Limeにはいくつかの制御フロー構文があります: if/elif/else、while、for、matchです。

<!--
### if / elif / else
-->

### if / elif / else

<!--
The `if` expression allows you to branch your code depending on conditions.
Lime supports `elif` for chaining multiple conditions without nesting.
-->

`if`式は条件に応じてコードを分岐させることができます。Limeはネストなしで
複数の条件を連結する`elif`をサポートしています。

```lime
fn classify(int: x):
    if x > 0:
        return "positive"
    elif x < 0:
        return "negative"
    else:
        return "zero"

fn main():
    println(classify(5))    // positive
    println(classify(-3))   // negative
    println(classify(0))    // zero
    return
```

<!--
The condition must be a boolean. The `else` branch is optional.
-->

条件はブール値である必要があります。`else`分岐はオプションです。

<!--
### while
-->

### while

<!--
`while` loops repeat a block of code as long as a condition is true.
-->

`while`ループは条件がtrueの間、コードブロックを繰り返し実行します。

```lime
let mut i = 0
while i < 3:
    println(i)
    i = i + 1
```

<!--
> Note: Lime does not currently support `break` or `continue` in `while` loops.
-->

> 注釈: Limeは現在`while`ループ内で`break`または`continue`をサポートしていません。

<!--
### for
-->

### for

<!--
`for` iterates over a list or over an integer range `a..b` (from `a`
inclusive to `b` exclusive).
-->

`for`はリストまたは整数範囲`a..b`（`a`以上`b`未満）を反復します。

```lime
for n in [10, 20, 30]:
    println(n)

for i in 0..3:
    println(i)
```

<!--
### Range Expressions
-->

### 範囲式

<!--
Range expressions `a..b` create a range from `a` inclusive to `b` exclusive.
-->

範囲式`a..b`は`a`以上`b`未満の範囲を作成します。

<!--
### match
-->

### match

<!--
`match` destructures a value against patterns. It must be exhaustive — all
variants must be covered.
-->

`match`は値をパターンに対して分解します。網羅的である必要があります — すべての
バリアントをカバーする必要があります。

```lime
match Some(5):
    Some(v):
        println(v)
    None:
        println("none")
```

<!--
The patterns include:
-->

パターンには以下が含まれます:

- `try (a, b)` — タプルパターン（ネストされたパターンも許可）
- `catch:` — 捕捉すべて、何にでもマッチ
- `Some(v)` / `None` — `Option`バリアント
- `Variant(a, b)` — 構造体ライクなstate/enumバリアント

<!--
There is no `else` arm: `match` must be exhaustive.
-->

`else`分岐はありません: `match`は網羅的である必要があります。

<!--
### defer
-->

### defer

<!--
`defer:` schedules a block to run when the current function returns. Multiple
defers run in the order they were scheduled.
-->

`defer:`は現在の関数が返るときに実行されるブロックをスケジュールします。
複数のdeferはスケジュールされた順序で実行されます。

```lime
fn main():
    defer:
        println("cleanup")
    println("before")
    return
```

<!--
Output:
-->

出力:

```
before
cleanup
```
