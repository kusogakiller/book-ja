/*
## The Challenger Runtime
*/

## Challengerランタイム

<!--
Challenger is Lime's single-threaded native async runtime. It provides an
executor, task management, channels, synchronization primitives, TCP
networking, and timers — all implemented in C99 with no GC and no runtime
overhead.
-->

ChallengerはLimeのシングルスレッドネイティブasyncランタイムです。
エグゼキュータ、タスク管理、チャネル、同期プリミティブ、TCPネットワーキング、
タイマーを提供します — すべてC99で実装され、GCなし、ランタイムオーバーヘッドなしです。

<!--
### Executor
-->

### エグゼキュータ

<!--
The executor is the core of Challenger. It manages a ready queue of tasks
and polls them cooperatively. Each task is a future that returns `Poll::Ready`
or `Poll::Pending`.
-->

エグゼキュータはChallengerの核です。タスクの準備キューを管理し、協調的にpollします。
各taskは`Poll::Ready`または`Poll::Pending`を返すfutureです。

<!--
### Task States
-->

### タスクの状態

<!--
Each task progresses through these states:
-->

各タスクは以下の状態を遷移します:

| 状態 | 説明 |
|------|------|
| `READY` | 実行待ちキューに入っている |
| `RUNNING` | 現在pollされている |
| `COMPLETED` | 完了 |
| `CANCELLED` | キャンセルされた |

<!--
### Spawning Tasks
-->

### タスクのスポーン

<!--
`spawn` creates a new task on the executor and returns its ID:
-->

`spawn`はエグゼキュータに新しいタスクを作成し、そのIDを返します:

```lime
lime background_work():
    let i = 0
    while i < 100:
        yield_now
        i = i + 1
    return

fn main():
    let id = spawn(background_work())
    println("task " + str(id) + " spawned")
    // mainの実行は継続
    return
```

<!--
### Cancelling Tasks
-->

### タスクのキャンセル

<!--
`cancel` removes a task from the executor by its ID. Cancelling a completed
task is a no-op. Cancelling a nonexistent task is also safe.
-->

`cancel`はタスクIDでエグゼキュータからタスクを除去します。完了済みタスクのキャンセルは
無操作です。存在しないタスクのキャンセルも安全です。

```lime
fn main():
    let id = spawn(some_work())
    cancel(id)
    return
```

<!--
### Yielding
-->

### ユィールド

<!--
`yield_now` is a cooperative yield point. When a task calls `yield_now`,
it returns `Pending` and is re-enqueued into the ready queue. The executor
then polls the next task.
-->

`yield_now`は協調的なyieldポイントです。タスクが`yield_now`を呼ぶと、
`Pending`を返して準備キューに再 enqueueされます。エグゼキュータは次のタスクをpollします。

```lime
lime cooperative_task():
    let i = 0
    while i < 10:
        println("step " + str(i))
        yield_now
        i = i + 1
    return
```

<!--
### Async Sleep
-->

### 非同期スリープ

<!--
`sleep(ms)` asynchronously waits for `ms` milliseconds. The task becomes
`Pending` and is woken by the timer wheel when the deadline expires.
-->

`sleep(ms)`は`ms`ミリ秒だけ非同期的に待機します。タスクは`Pending`になり、
デッドラインが期限切れになるとタイマーホイールによってwakeされます。

```lime
lime delayed():
    await sleep(500)   // 500ms 待機
    println("after delay")
    return
```
