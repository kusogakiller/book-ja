/*
## Data Types
*/

## データ型

<!--
Lime is a statically-typed language. Every value has a specific type, and the
compiler determines the type at compile time. Lime has several built-in types.
-->

Limeは静的型付き言語です。すべての値には特定の型があり、コンパイラはコンパイル時に型を
決定します。Limeにはいくつかの組み込み型があります。

<!--
### Primitive Types
-->

### プリミティブ型

| 型 | エイリアス | 説明 |
|------|---------|-------|
| `int` | `i32`, `i` | 64ビット符号付き整数 |
| `long` | `i64`, `l` | 64ビット整数。リテラルには`L`サフィックスを使用 |
| `float` | `f64`, `f` | 64ビット浮動小数点数 |
| `bool` | `i1`, `b` | `true` / `false` |
| `str` | `s` | 文字列（UTF-8、不変） |
| `json` | — | ファーストクラスのJSON値 |

<!--
### Integer Literals
-->

### 整数リテラル

<!--
Integer literals: `42`, `-1`. Long literals carry an `L` suffix: `42L`.
-->

整数リテラル: `42`、`-1`。longリテラルには`L`サフィックスを使用します: `42L`。

<!--
### Float Literals
-->

### 浮動小数点リテラル

<!--
Float literals need digits on both sides of the dot: `3.14`, but `.5` is not
accepted.
-->

浮動小数点リテラルはドットの両側に数字が必要です: `3.14`ですが、`.5`は
受け付けられません。

<!--
### Boolean Literals
-->

### ブールリテラル

<!--
Boolean literals are `true` and `false`.
-->

ブールリテラルは`true`と`false`です。

<!--
### String Literals
-->

### 文字列リテラル

<!--
String literals use double quotes: `"hello"`. Standard escapes such as `\n`
and `\t` work inside strings.
-->

文字列リテラルは二重引用符を使用します: `"hello"`。`\n`や`\t`などの
標準エスケープは文字列内で動作します。

<!--
### Compound Types
-->

### 複合型

<!--
Lime has several compound types:
-->

Limeにはいくつかの複合型があります:

- `Option(T)` または短縮形 `T?` — 型`T`の値か無しのいずれか
- `Result(T, E)` — 成功値`T`かエラー値`E`のいずれか
- `List(T)` — `T`の成長可能なリスト
- `HashMap(K, V)` — ハッシュマップ
- `HashSet(T)` — ハッシュセット
- タプル `(A, B, C)` — 固定サイズの異種型シーケンス

<!--
### Option
-->

### Option

<!--
`Option(T)` represents an optional value. Values are written `Some(value)` or
`None`.
-->

`Option(T)`はオプショナルな値を表します。値は`Some(value)`または`None`と書きます。

```lime
let Option(int): maybe = Some(10)
let maybe2 = None
```

<!--
### Result
-->

### Result

<!--
`Result(T, E)` represents either success (`Success(value)`) or failure
(`Error(error)`). It is defined as a `state` type and is used for error
handling.
-->

`Result(T, E)`は成功（`Success(value)`）か失敗（`Error(error)`）のいずれかを表します。
`state`型として定義されており、エラー処理に使用します。

```lime
state Result(T, E):
    Success(T)
    Error(E)

let Result(int, str): ok = Success(42)
let Result(int, str): err = Error("something went wrong")
```

<!--
### Tuples
-->

### タプル

<!--
Tuples are fixed-size heterogeneous sequences. Access elements by index:
-->

タプルは固定サイズの異種型シーケンスです。インデックスで要素にアクセスします:

```lime
let pair = (1, "one")
match pair:
    try (a, b):
        println(a)   // 1
        println(b)   // one
```

<!--
Note that a typed annotation for a tuple (`let (int, str): pair = ...`) is not
accepted; tuples are bound without a type annotation.
-->

タプルの型付き注釈（`let (int, str): pair = ...`）は受け付けられません。
タプルは型注釈なしでバインドします。

<!--
### Lists
-->

### リスト

<!--
Lists are growable sequences. Empty lists need a type annotation:
-->

リストは成長可能なシーケンスです。空のリストには型注釈が必要です:

```lime
let List(int): nums = []
let xs = [1, 2, 3]
let ys = ["a", "b"]
```

<!--
### Type Conversions
-->

### 型変換

<!--
Conversions use function syntax: `int(x)`, `float(x)`, and `str(x)`.
-->

変換には関数シンタックスを使用します: `int(x)`、`float(x)`、`str(x)`です。

```lime
println(int("42"))    // 42
println(float(7))     // 7
println(str(3.14))    // 3.14
```

<!--
`len(x)` returns the byte length of a string or the length of a list.
-->

`len(x)`は文字列のバイト長またはリストの長さを返します。
