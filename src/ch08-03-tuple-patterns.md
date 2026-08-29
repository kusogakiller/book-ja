/*
## Tuple Pattern Matching
*/

## タプルのパターンマッチング

<!--
Lime supports pattern matching on tuples using the `try` keyword. The bare
`(a, b)` form is not accepted — tuple arms must be written as `try (a, b)`.
-->

Limeは`try`キーワードを使用したタプルのパターンマッチングをサポートしています。
bareな`(a, b)`形式は受け付けられません — タプル分岐は`try (a, b)`と書く必要があります。

```lime
let t = (1, 2)
match t:
    try (x, y):
        println(x + y)   // 3
    catch:
        println("wildcard")
```

<!--
### Nested Tuple Patterns
-->

### ネストされたタプルパターン

<!--
Tuple patterns can be nested:
-->

タプルパターンはネストできます:

```lime
let n = (10, (20, 30))
match n:
    try (x, (y, z)):
        println(x + y + z)   // 60
```

<!--
### Generic Swap Function
-->

### ジェネリックswap関数

<!--
A generic swap function that returns a tuple:
-->

タプルを返すジェネリックswap関数:

```lime
fn swap(T, U)(T: a, U: b):
    return (b, a)

fn main():
    let s = swap(1, "hi")
    match s:
        try (b, a):
            println(a)   // hi
            println(b)   // 1
    return
```

<!--
### Wildcard in Tuple Patterns
-->

### タプルパターンのワイルドカード

<!--
Use `catch:` to match anything not explicitly matched:
-->

明示的にマッチしないすべてにマッチするには`catch:`を使用します:

```lime
let w = (7, "seven")
match w:
    catch:
        println("wildcard")
```
