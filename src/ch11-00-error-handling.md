# エラー処理

<!--
Error handling is an important part of any programming language. Lime has a
different approach to error handling compared to languages like Rust. Lime does
not have `panic!` or `Result` in the Rust sense.
-->

エラー処理はあらゆるプログラミング言語において重要な部分です。LimeはRustなどの
言語とは異なるアプローチを採用しています。LimeにはRustの`panic!`や`Result`がありません。

<!--
### Runtime Errors
-->

### ランタイムエラー

<!--
When the interpreter encounters an error during execution, it produces a
runtime error:
-->

インタプリタが実行中にエラーに遭遇すると、ランタイムエラーが発生します:

```
error[E0601] hello.lime:2:1
Runtime error: undefined variable 'xyz'
```

<!--
### Type Errors
-->

### 型エラー

<!--
The type checker catches errors at compile time:
-->

型チェックはコンパイル時にエラーを捕捉します:

```
error[E0201] hello.lime:2:1
  |
2 | println(xyz)
  | ^
Type error: undefined variable 'xyz'
  = help: did you mean 'x'?
```

<!--
### Using State for Error Handling
-->

### stateを使用したエラー処理

<!--
You can use `state` types to model errors explicitly:
-->

`state`型を使用してエラーを明示的にモデル化できます:

```lime
state Result:
    Success(int)
    Error(str)

fn divide(int: a, int: b):
    if b == 0:
        return Error("division by zero")
    else:
        return Success(a / b)

fn main():
    let r = divide(10, 2)
    match r:
        Success(v):
            println(v)
        Error(msg):
            println(msg)
    return
```

<!--
### Error Codes
-->

### エラーコード

<!--
Lime uses error codes for diagnostic messages. The main categories are:
-->

Limeは診断メッセージにエラーコードを使用します。主なカテゴリは以下の通りです:

| コード範囲 | カテゴリ |
|------------|----------|
| `E0001` | レキサーエラー（トークン化の失敗） |
| `E0101` | パーサーエラー（構文エラー） |
| `E0200`–`E0226` | 型エラー |
| `E0401`–`E0402` | コード生成エラー |
| `E0501` | ビルド/リンカーエラー |
| `E0601` | ランタイムエラー |
| `E0701` | メモリ分析エラー |
