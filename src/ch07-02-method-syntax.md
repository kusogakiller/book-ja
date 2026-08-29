/*
## Method Syntax
*/

## メソッド記法

<!--
Methods are functions that are defined within the context of a struct (or
enum). They receive `self` as their first parameter (automatically), but
in Lime the syntax is different from Rust.
-->

メソッドは構造体（またはenum）のコンテキスト内で定義された関数です。
Rustとは異なり、Limeではメソッドは構造体内に直接記述します。

```lime
struct Point:
    int: x
    int: y
    fn magnitude():
        return x * x + y * y

fn main():
    let p = Point(3, 4)
    println(p.x)          // 3
    println(p.magnitude())  // 25
    return
```

<!--
### Methods with Arguments
-->

### 引数を持つメソッド

<!--
Methods can take arguments, including the struct itself:
-->

メソッドは構造体自体を含む引数を取ることができます:

```lime
struct Point:
    int: x
    int: y
    fn distance():
        return x * x + y * y
```

<!--
Methods are called using dot notation on the instance:
-->

メソッドはインスタンスに対してドット記法で呼び出します:

```lime
let p = Point(3, 4)
println(p.distance())
```
