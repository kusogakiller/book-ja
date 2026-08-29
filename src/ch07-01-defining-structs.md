/*
## Defining and Instantiating Structs
*/

## 構造体を定義し、インスタンス化する

<!--
Structs are defined with the `struct` keyword followed by the name of the
struct and a block of field declarations.
-->

構造体は`struct`キーワード、構造体名、フィールド宣言のブロックで定義します。

```lime
struct Point:
    int: x
    int: y
```

<!--
Each field declaration consists of a type and a name, separated by a colon.
-->

各フィールド宣言は、型と名前をコロンで区切ったものです。

<!--
### Struct Construction
-->

### 構造体の構築

<!--
Create an instance of a struct by calling the struct name as a function,
passing values for each field in order:
-->

構造体名を関数として呼び出し、各フィールドの値を順番に渡してインスタンスを作成します:

```lime
let p = Point(3, 4)
```

<!--
You can also name the fields when constructing:
-->

構築時にフィールド名を指定することもできます:

```lime
let p = Point(3, 4)
```

<!--
### Example: A Task Struct
-->

### 例: Task構造体

```lime
struct Task:
    int: id
    str: title
    int: priority

fn main():
    let t = Task(1, "write audit", 7)
    println(t.id)           // 1
    println(t.title)        // write audit
    println(t.priority)     // 7
```
