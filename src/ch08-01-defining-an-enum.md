/*
## Defining an Enum
*/

## Enumを定義する

<!--
### state
-->

### state

<!--
`state` declares variants without typed fields:
-->

`state`は型付きフィールドのないバリアントを宣言します:

```lime
state Direction:
    North
    South
    East
    West
```

<!--
Creating and using state variants:
-->

stateバリアントの作成と使用:

```lime
let d = North
match d:
    North:
        println("going north")
    South:
        println("going south")
    catch:
        println("other")
```

<!--
### enum
-->

### enum

<!--
`enum` declares variants with typed fields:
-->

`enum`は型付きフィールドを持つバリアントを宣言します:

```lime
enum Shape:
    Circle(float: radius)
    Rectangle(float: width, float: height)
```

<!--
Creating and using enum variants:
-->

enumバリアントの作成と使用:

```lime
fn area(Shape: s):
    match s:
        Circle(r):
            return 3.14 * r * r
        Rectangle(w, h):
            return w * h

fn main():
    let c = Circle(5.0)
    println(area(c))   // 78.5
    return
```

<!--
### Mixed Variants
-->

### 混合バリアント

<!--
Enums can mix bare variants and typed variants:
-->

Enumはbareバリアントと型付きバリアントを混在させることができます:

```lime
enum State:
    Todo
    Running
    Done
    Failed(int)

fn label(State: s):
    match s:
        Todo:
            println("Todo")
        Running:
            println("Running")
        Done:
            println("Done")
        Failed(code):
            println("Failed")
            println(code)

fn main():
    let a = Todo
    let d = Failed(503)
    label(a)
    label(d)
```

<!--
### Option and Result
-->

### OptionとResult

<!--
Lime has built-in `Option(T)` and `Result(T, E)` types:
-->

Limeには組み込みの`Option(T)`と`Result(T, E)`型があります:

```lime
let Option(int): maybe = Some(10)
let maybe2 = None
```
