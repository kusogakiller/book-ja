/*
## Async and Await
*/

## asyncとawait

<!--
Lime provides async/await support for asynchronous programming. Functions
declared with the keyword `lime` instead of `fn` are async functions. Lime
includes **Challenger**, a single-threaded native async runtime with an
executor, channels, synchronization primitives, TCP, and timers.
-->

Limeは非同期プログラミングのためのasync/awaitサポートを提供します。
`fn`の代わりに`lime`キーワードで宣言された関数は非同期関数です。
Limeには**Challenger**が含まれています。これはエグゼキュータ、チャネル、
同期プリミティブ、TCP、タイマーを備えたシングルスレッドのネイティブasyncランタイムです。

<!--
### Defining Async Functions
-->

### 非同期関数の定義

<!--
Async functions use the `lime` keyword instead of `fn`:
-->

非同期関数は`fn`の代わりに`lime`キーワードを使用します:

```lime
lime double(int: n):
    return n * 2

lime greet(str: name):
    return "Hello, " + name
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
    let msg = await greet("Lime")
    println(msg)      // Hello, Lime
    return
```

<!--
### Spawning Tasks
-->

### タスクのスポーン

<!--
Use `spawn` to run a future on the executor without blocking the current
task. `spawn` returns a task ID that can be used with `cancel`.
-->

`spawn`を使用して、現在のタスクをブロックせずにエグゼキュータ上でfutureを実行します。
`spawn`はタスクIDを返し、`cancel`で使用できます。

```lime
lime compute(int: n):
    return n * n

fn main():
    let task_id = spawn(compute(10))
    println("task spawned: " + str(task_id))
    return
```

<!--
### Cancelling Tasks
-->

### タスクのキャンセル

<!--
Cancel a running or pending task by its ID:
-->

タスクIDを使用して実行中または保留中のタスクをキャンセルします:

```lime
fn main():
    let id = spawn(some_async_work())
    cancel(id)
    return
```

<!--
### Yielding
-->

### ユィールド

<!--
`yield_now` cooperatively yields control back to the executor, allowing
other tasks to run:
-->

`yield_now`は協調的にエグゼキュータに制御を返し、他のタスクを実行させます:

```lime
lime worker():
    let i = 0
    while i < 10:
        yield_now
        i = i + 1
    return
```

<!--
### Async Sleep
-->

### 非同期スリープ

<!--
`sleep` asynchronously waits for a specified number of milliseconds:
-->

`sleep`は指定されたミリ秒数だけ非同期的に待機します:

```lime
lime slow():
    await sleep(100)   // 100ms 待機
    return "done"
```

<!--
### Single-Threaded Runtime
-->

### シングルスレッドランタイム

<!--
Challenger is a single-threaded, poll-based async runtime. The executor
runs one task at a time, polling futures until they complete. Tasks are
scheduled cooperatively — a task must explicitly `await` or `yield_now`
to give other tasks a chance to run.
-->

Challengerはシングルスレッドのpollベースasyncランタイムです。
エグゼキュータは一度に1つのタスクを実行し、futureが完了するまでpollし続けます。
タスクは協調的にスケジュールされます — タスクは明示的に`await`または`yield_now`
を行い、他のタスクに実行機会を与える必要があります。
