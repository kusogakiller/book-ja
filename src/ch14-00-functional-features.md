# 関数型言語の機能：クロージャ

<!--
Closures are a fundamental feature in Lime. They allow you to create anonymous
functions that can capture variables from their surrounding scope.
-->

クロージャはLimeの基本的な機能です。周囲のスコープから変数をキャプチャできる
匿名関数を作成できます。

<!--
### Closures: Anonymous Functions that Capture Their Environment
-->

### クロージャ：環境をキャプチャする匿名関数

<!--
Closures are created using the `fn` keyword without a name. They can capture
variables from their enclosing scope by value.
-->

クロージャは名前なしの`fn`キーワードを使用して作成します。閉じられたスコープから
値によって変数をキャプチャできます。

```lime
fn main():
    let add10 = fn(int: x):
        return x + 10
    println(add10(5))    // 15

    let numbers = [1, 2, 3]
    let doubled = numbers.map(fn(int: x): return x * 2)
    println(doubled)     // [2, 4, 6]
    return
```

<!--
### Returning Closures from Functions
-->

### 関数からクロージャを返す

<!--
Functions can return closures, which is useful for creating function factories:
-->

関数はクロージャを返すことができ、関数ファクトリの作成に便利です:

```lime
fn make_adder(int: n):
    return fn(int: x):
        return x + n

fn main():
    let add10 = make_adder(10)
    let add20 = make_adder(20)
    println(add10(5))    // 15
    println(add20(5))    // 25
    return
```

<!--
### Capture by Value
-->

### 値によるキャプチャ

<!--
Closures capture variables by value (immutable copies). Mutable capture is
not supported.
-->

クロージャは値によって変数をキャプチャします（不変のコピー）。可変キャプチャは
サポートされていません。

```lime
fn main():
    let factor = 10
    let multiply = fn(int: x):
        return x * factor
    println(multiply(3))   // 30
    return
```
