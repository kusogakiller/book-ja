/*
## Strings
*/

## 文字列

<!--
Strings are one of the most commonly used data types in any programming
language. Lime strings are UTF-8 encoded and immutable.
-->

文字列はあらゆるプログラミング言語で最も一般的に使用されるデータ型の一つです。
Limeの文字列はUTF-8エンコードで不変です。

<!--
### String Literals
-->

### 文字列リテラル

<!--
String literals use double quotes:
-->

文字列リテラルは二重引用符を使用します:

```lime
let str: text = "Hello Lime"
```

<!--
### String Methods
-->

### 文字列メソッド

<!--
Strings support several methods. Methods are non-mutating; they return new
strings rather than changing the receiver.
-->

文字列はいくつかのメソッドをサポートしています。メソッドは不変で、
レシーバーを変更するのではなく新しい文字列を返します。

```lime
let str: text = "Hello Lime"
println(text.length())     // 10 (characters)
println(text.to_upper())   // HELLO LIME
println(text.to_lower())   // hello lime
println(text.repeat(2))    // Hello LimeHello Lime
println(text.slice(0, 5))  // Hello
println(text.len())        // 10 (bytes)
```

<!--
The methods available on strings are `len`, `byte_len`, `length`, `chars`,
`bytes`, `slice`, `to_upper`, `to_lower`, `repeat`, `read`, `write`, `exists`,
`remove`, `append`, and `metadata`.
-->

文字列で使用できるメソッドは`len`、`byte_len`、`length`、`chars`、
`bytes`、`slice`、`to_upper`、`to_lower`、`repeat`、`read`、`write`、
`exists`、`remove`、`append`、`metadata`です。

<!--
### String Module
-->

### stringモジュール

<!--
The `string` package provides additional string operations. It requires a
`citrus.toml` project with `[import] string = "v0.1.0"`:
-->

`string`パッケージは追加の文字列操作を提供します。`citrus.toml`プロジェクトで
`[import] string = "v0.1.0"`が必要です:

```lime
let str: s = "  Hello, Lime  "
println(string.trim(s))          // Hello, Lime
println(string.to_upper(s))      //   HELLO, LIME
println(string.contains(s, "Li"))  // true
println(string.starts_with(s, "  He"))  // true
println(string.ends_with(s, "  "))      // true
println(string.replace("a-b-c", "-", "_"))  // a_b_c
println(string.repeat("ab", 3))            // ababab
let List(str): parts = string.split("x,y,z", ",")
println(parts)                            // [x, y, z]
```

<!--
### String Concatenation
-->

### 文字列連結

<!--
The `+` operator concatenates strings:
-->

`+`演算子は文字列を連結します:

```lime
let t = "hello"
println(t + " world")   // hello world
```

<!--
### StringBuilder
-->

### StringBuilder

<!--
StringBuilder appends incrementally:
-->

StringBuilderは增量的に追加します:

```lime
let sb = StringBuilder()
sb.add("a")
sb.add("b")
println(sb.build())   // ab
```

<!--
### len vs length
-->

### lenとlengthの違い

<!--
`len(s)` gives the byte length; `.length()` gives the character count. For
ASCII text they agree.
-->

`len(s)`はバイト長を、`.length()`は文字数を返します。ASCIIテキストでは一致します。
