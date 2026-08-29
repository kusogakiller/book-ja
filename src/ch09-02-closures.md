/*
## Closures
*/

## クロージャ

<!--
Closures are anonymous function expressions that can capture variables from
their surrounding scope. They can be stored in variables and passed as
arguments.
-->

クロージャは周囲のスコープから変数をキャプチャできる匿名関数式です。
変数に格納し、引数として渡すことができます。

<!--
### Basic Closures
-->

### 基本的なクロージャ

```lime
fn main():
    let double = fn(int: x):
        return x * 2
    println(double(5))   // 10
    return
```

<!--
### Using Closures with Methods
-->

### メソッドでのクロージャ使用

```lime
fn main():
    let numbers = [1, 2, 3]
    let doubled = numbers.map(fn(int: x): return x * 2)
    println(doubled)     // [2, 4, 6]
    return
```

<!--
### Capturing Variables
-->

### 変数のキャプチャ

<!--
Closures capture variables from their surrounding scope by value:
-->

クロージャは周囲のスコープから値によって変数をキャプチャします:

```lime
fn main():
    let factor = 10
    let multiply = fn(int: x):
        return x * factor
    println(multiply(3))   // 30
    return
```

<!--
### Returning Closures from Functions
-->

### 関数からクロージャを返す

<!--
Functions can return closures:
-->

関数はクロージャを返すことができます:

```lime
fn make_adder(int: n):
    return fn(int: x):
        return x + n

fn main():
    let add10 = make_adder(10)
    println(add10(5))    // 15
    println(add10(90))   // 100
    return
```

<!--
### Capture Mechanism
-->

### キャプチャメカニズム

<!--
Closures capture variables by value (immutable). Mutable capture is not
supported. Captured values are packed into a heap-allocated array and passed
to the closure function.
-->

クロージャは値によって変数をキャプチャします（不変）。可変キャプチャは
サポートされていません。キャプチャされた値はヒープ割り当ての配列にパックされ、
クロージャ関数に渡されます。

<!--
### Closures with No Arguments
-->

### 引数なしクロージャ

```lime
fn main():
    let greet = fn():
        return "hello"
    println(greet())   // hello
    return
```

<!--
### Closures with Untyped Parameters
-->

### 型なし引数のクロージャ

<!--
When parameter types are omitted, they are inferred from usage:
-->

引数の型を省略すると、使用状況から推論されます:

```lime
fn main():
    let f = fn(x): return x + 1
    println(f(10))   // 11
    return
```
