/*
## Closures: Anonymous Functions that Capture Their Environment
*/

## クロージャ：環境をキャプチャする匿名関数

<!--
Closures provide a way to capture the environment in which they are defined.
This is powerful for writing concise, expressive code.
-->

クロージャは、定義された環境をキャプチャする方法を提供します。
これは簡潔で表現力豊かなコードを書くために強力です。

<!--
### Closure Syntax
-->

### クロージャ構文

```lime
fn main():
    let greet = fn(str: name):
        return "Hello, " + name
    println(greet("Lime"))   // Hello, Lime
    return
```

<!--
### Using Closures with List Methods
-->

### リストメソッドでのクロージャ使用

```lime
fn main():
    let nums = [1, 2, 3, 4, 5]
    let evens = nums.filter(fn(int: x): return x % 2 == 0)
    println(evens)   // [2, 4]

    let total = nums.reduce(fn(int: acc, int: x): return acc + x, 0)
    println(total)   // 15
    return
```

<!--
### Closures as Function Parameters
-->

### 関数パラメータとしてのクロージャ

```lime
fn apply(int: x, fn(int): f):
    return f(x)

fn main():
    let result = apply(5, fn(int: x): return x * 2)
    println(result)   // 10
    return
```
