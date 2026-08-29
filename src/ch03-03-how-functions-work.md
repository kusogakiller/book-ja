/*
## Functions
*/

## 関数

<!--
Functions are declared at the top level with `fn`. Parameters are written
`Type: name` and are separated by commas. There is no return type in the
signature; the return type is inferred.
-->

関数はトップレベルで`fn`で宣言します。パラメータは`Type: name`と書き、
カンマで区切ります。シグネチャには戻り型はありません。戻り型は推論されます。

```lime
fn add(int: a, int: b):
    return a + b

fn main():
    println(add(1, 2))
    return
```

<!--
### Untyped Parameters
-->

### 型なしパラメータ

<!--
Parameters may be left untyped; their type is inferred from call sites and the
body:
-->

パラメータは型なしにできます。型は呼び出し元と本体から推論されます:

```lime
fn identity(value):
    return value

fn main():
    println(identity("works"))
    return
```

<!--
### Return Values
-->

### 戻り値

<!--
A function returns with `return expr`. You may annotate the return type
explicitly, but it must still match the expression:
-->

関数は`return expr`で戻ります。戻り型を明示的に注釈できますが、
式と一致する必要があります:

```lime
fn f():
    return int: 42
```

<!--
A bare `return` (with no expression) ends the function and returns the unit
value. A function whose last statement is a plain expression implicitly
returns that expression's value.
-->

`return`（式なし）は関数を終了し、ユニット値を返します。最後の文が通常の式の
関数は、その式の値を暗黙的に返します。

<!--
### Recursion
-->

### 再帰

<!--
Functions can call themselves (and each other); all functions in a file are
visible to one another regardless of declaration order.
-->

関数は自分自身（および相互に）を呼び出すことができます。ファイル内のすべての関数は、
宣言順序に関係なく互いに参照できます。

```lime
fn fact(int: n):
    if n <= 1:
        return 1
    else:
        return n * fact(n - 1)

fn main():
    println(fact(5))
    return
```

<!--
### No Return Type Annotation in Signature
-->

### シグネチャに戻り型の注釈なし

<!--
Lime functions do not include a return type in the function signature. The
return type is always inferred from the function body. This is different from
languages like Rust where the return type is explicit.
-->

Lime関数の関数シグネチャには戻り型を含めません。戻り型は常に関数本体から
推論されます。これはRustのような戻り型が明示的な言語とは異なります。
