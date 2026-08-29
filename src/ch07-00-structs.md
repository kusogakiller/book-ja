/*
## Using Structs to Structure Related Data
*/

## 構造体を使用して関係のあるデータを構造化する

<!--
Structs are a way to create custom data types by grouping together related
fields. Lime structs can also have methods.
-->

構造体は、関連するフィールドをまとめて独自のデータ型を作成する方法です。
Limeの構造体にはメソッドも持たせることができます。

<!--
### Defining Structs
-->

### 構造体の定義

<!--
Structs are defined using the `struct` keyword:
-->

構造体は`struct`キーワードを使用して定義します:

```lime
struct Point:
    int: x
    int: y
```

<!--
### Creating Instances
-->

### インスタンスの作成

<!--
Create an instance by calling the struct name as a function:
-->

構造体名を関数として呼び出してインスタンスを作成します:

```lime
let p = Point(3, 4)
```

<!--
### Accessing Fields
-->

### フィールドへのアクセス

<!--
Access fields using dot notation:
-->

ドット記法でフィールドにアクセスします:

```lime
let p = Point(3, 4)
println(p.x)   // 3
println(p.y)   // 4
```

<!--
### Updating a Struct Instance
-->

### 構造体インスタンスの更新

<!--
You can create a new instance by using the old instance's values:
-->

古いインスタンスの値を使用して新しいインスタンスを作成できます:

```lime
struct Task:
    int: id
    str: title
    int: priority

fn main():
    let t = Task(1, "write audit", 7)
    let bumped = Task(t.id, t.title, t.priority + 3)
    println(bumped.priority)   // 10
```
