/*
## Variables and Mutability
*/

## 変数と可変性

<!--
Variables are one of the most basic concepts in programming. In Lime, you use
`let` to bind a value to a name. Bindings are immutable by default; add `mut`
to allow reassignment.
-->

変数はプログラミングにおいて最も基本的な概念のひとつです。Limeでは、`let`を使用して
値を名前にバインドします。バインディングはデフォルトで不変です。再代入を許可するには
`mut`を追加してください。

<!--
### Variable Bindings
-->

### 変数バインディング

<!--
Use `let` to create a variable binding. The type is normally inferred:
-->

`let`を使用して変数バインディングを作成します。型は通常推論されます:

```lime
let x = 10
let name = "lime"
let price = 19.5
let flag = true
```

<!--
### Mutability
-->

### 可変性

<!--
By default, variable bindings are immutable. To make a binding mutable, add
`mut` before the variable name:
-->

デフォルトでは、変数バインディングは不変です。バインディングを可変にするには、
変数名の前に`mut`を追加してください:

```lime
let mut total = 0
total = total + 10
```

<!--
Trying to reassign a non-mutable binding will result in a compile-time error:
-->

不変のバインディングを再代入しようとすると、コンパイル時エラーが発生します:

```lime
let x = 10
x = 20  // error[E02xx]: cannot reassign to immutable variable
```

<!--
### Type Annotations
-->

### 型注釈

<!--
The type of a binding is normally inferred. You can write the type explicitly
between the `let` and the name, separated by a colon:
-->

バインディングの型は通常推論されます。`let`と名前の間にコロンで区切って型を
明示的に記述できます:

```lime
let int: x = 10
let str: name = "lime"
let List(int): nums = [1, 2, 3]
```

<!--
Type aliases are accepted in this position (`let i32: x = 10`). The `Option`
shorthand (`T?`) also works as an annotation.
-->

この位置では型エイリアスも受け付けられます（`let i32: x = 10`）。`Option`
の短縮形（`T?`）も注釈として機能します。

<!--
### Memory Placement
-->

### メモリ配置

<!--
An explicit memory placement can be requested after the type:
-->

型の後に明示的なメモリ配置を指定できます:

```lime
let int(heap): x = 10
let int(stack): y = 20
```

<!--
This is an advanced hint and not required for most programs.
-->

これは高度なヒントであり、ほとんどのプログラムでは必要ありません。

<!--
### Compound Assignment
-->

### 複合代入

<!--
Assignments use `=`. The compound operators (`+=`, `-=`, `*=` and `/=`) are
tokenized but not yet accepted by the parser — use the long form:
-->

代入には`=`を使用します。複合演算子（`+=`、`-=`、`*=`、`/=`）はトークン化されますが、
パーサーではまだ受け付けられません — 長い形式を使用してください:

```lime
let mut n = 1
n = n + 1
```
