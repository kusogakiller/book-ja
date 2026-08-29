/*
## Defining Functions
*/

## 関数の定義

<!--
Functions are declared with `fn`. Parameters are written `Type: name`.
-->

関数は`fn`で宣言します。パラメータは`Type: name`と書きます。

```lime
fn add(int: a, int: b):
    return a + b

fn main():
    println(add(1, 2))   // 3
    return
```

<!--
### Multiple Return Values via Tuples
-->

### タプルによる複数の戻り値

<!--
Functions can return tuples to return multiple values:
-->

関数はタプルを返すことで複数の値を返すことができます:

```lime
fn swap(T, U)(T: a, U: b):
    return (b, a)

fn main():
    let s = swap(1, "hi")
    println(s)   // (hi, 1)
    return
```

<!--
### Untyped Parameters
-->

### 型なしパラメータ

<!--
Parameters may be left untyped:
-->

パラメータは型なしにできます:

```lime
fn double(x):
    return x * 2

fn main():
    println(double(5))    // 10
    println(double("hi")) // hihi
    return
```

<!--
### No Return Type in Signature
-->

### シグネチャに戻り型なし

<!--
Lime functions do not have a return type in the signature. The return type is
inferred from the function body.
-->

Lime関数のシグネチャには戻り型がありません。戻り型は関数本体から推論されます。
