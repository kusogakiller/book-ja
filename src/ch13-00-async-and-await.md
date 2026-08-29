/*
## Async and Await
*/

## asyncとawait

<!--
Lime provides async/await support for asynchronous programming. Functions
declared with the keyword `lime` instead of `fn` are async functions.
-->

Limeは非同期プログラミングのためのasync/awaitサポートを提供します。
`fn`の代わりに`lime`キーワードで宣言された関数は非同期関数です。

<!--
### Defining Async Functions
-->

### 非同期関数の定義

```lime
lime double(int: n):
    return n * 2
```

<!--
### Calling Async Functions
-->

### 非同期関数の呼び出し

<!--
Call async functions with `await`:
-->

`await`を使用して非同期関数を呼び出します:

```lime
fn main():
    let result = await double(21)
    println(result)   // 42
    return
```

<!--
### Current Limitations
-->

### 現在の制限事項

<!--
In the current interpreter, `await` runs the async function to completion
immediately (synchronously). There is no parallelism and no suspension.
-->

現在のインタプリタでは、`await`は非同期関数を即座に（同期的に）完了まで実行します。
並列化もサスペンドもありません。

<!--
The LLVM backend lowers `await` to a direct synchronous call, matching the
interpreter's synchronous execution. There is no async runtime, scheduler, or
coroutine lowering.
-->

LLVMバックエンドは`await`を直接の同期呼び出しにローワリングし、
インタプリタの同期実行と一致させます。非同期ランタイム、スケジューラ、
コルーチンのローワリングはありません。
