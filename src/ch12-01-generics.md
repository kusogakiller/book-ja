/*
## Generic Data Types
*/

## ジェネリックなデータ型

<!--
Generics allow you to define functions, structs, and enums that work with
multiple types.
-->

ジェネリクスでは複数の型で動作する関数、構造体、enumを定義できます。

<!--
### Generic Functions
-->

### ジェネリック関数

<!--
Generic functions declare type parameters between the name and the parameter
list:
-->

ジェネリック関数は、名前とパラメータリストの間に型パラメータを宣言します:

```lime
fn swap(T, U)(T: a, U: b):
    return (b, a)

fn main():
    let s = swap(1, "hi")
    println(s)   // (hi, 1)
    return
```

<!--
### Generic Structs
-->

### ジェネリック構造体

```lime
struct Box(T):
    T: value
    fn get():
        return value

fn main():
    let b = Box(7)
    println(b.get())   // 7
    return
```

<!--
### Generic Enums
-->

### ジェネリックenum

```lime
enum Maybe(T):
    Just(T)
    Nothing

fn main():
    let Maybe(int): m = Just(42)
    match m:
        Just(v):
            println(v)
        Nothing:
            println("nothing")
    return
```

<!--
### Type Constraints with Where Clause
-->

### Where節による型制約

<!--
Type parameters with constraints use the `Where` clause:
-->

型パラメータの制約には`Where`節を使用します:

```lime
fn max(List(T where T: Compare)): T:
    // ...
```
