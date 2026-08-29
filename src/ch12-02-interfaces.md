/*
## Interfaces: Defining Shared Behavior
*/

## インターフェース：共通の振る舞いを定義する

<!--
An interface declares a set of method signatures. A struct conforms to an
interface by declaring methods with the same names and types — no explicit
`implements` clause is needed. This is implicit implementation.
-->

インターフェースは一連のメソッドシグネチャを宣言します。構造体は同じ名前と型の
メソッドを宣言することでインターフェースに準拠します — 明示的な`implements`節は
必要ありません。これは暗黙的な実装です。

<!--
### Defining an Interface
-->

### インターフェースの定義

<!--
The signature syntax puts the return type after the parameter list, before
the colon:
-->

シグネチャ構文では、戻り型をパラメータリストの後、コロンの前に配置します:

```lime
interface Animal:
    fn speak(str): str:
    fn legs(): int:
```

<!--
### Implementing an Interface
-->

### インターフェースの実装

<!--
A struct conforms to an interface by declaring matching methods:
-->

構造体は一致するメソッドを宣言することでインターフェースに準拠します:

```lime
struct Dog:
    str: name
    int: legs
    fn speak(str):
        return "woof"
    fn legs():
        return 4

struct Cat:
    str: name
    int: legs
    fn speak(str):
        return "meow"
    fn legs():
        return 4
```

<!--
### Using Interface Types
-->

### インターフェース型の使用

<!--
A parameter typed as an interface accepts any struct that conforms to it:
-->

インターフェース型のパラメータは、それに準拠する任意の構造体を受け付けます:

```lime
fn make_sound(Animal: a):
    print(a.speak(""))

fn main():
    let d = Dog("Rex", 4)
    make_sound(d)   // woof
    let c = Cat("Mimi", 4)
    make_sound(c)   // meow
    return
```

<!--
### Operator Interfaces
-->

### 演算子インターフェース

<!--
Lime provides operator interfaces for user-defined types:
-->

Limeはユーザー定義型向けの演算子インターフェースを提供します:

| インターフェース | 演算子 | メソッド |
|-----------|-----------|---------|
| `Add` | `+` | `add` |
| `Equal` | `==` `!=` | `equal` |
| `Compare` | `<` `>` `<=` `>=` | `compare` |
