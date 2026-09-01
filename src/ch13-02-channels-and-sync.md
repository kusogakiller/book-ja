/*
## Channels and Synchronization
*/

## チャネルと同期

<!--
Challenger provides async channels and synchronization primitives for
communication and coordination between tasks.
-->

Challengerはタスク間の通信と協調のためのasyncチャネルと同期プリミティブを提供します。

<!--
### Bounded Channels
-->

### バウンドチャネル

<!--
Channels are bounded, async, and MPSC (multi-producer, single-consumer).
A channel with capacity 0 is unbounded.
-->

チャネルはバウンド、非同期、MPSC（マルチプロデューサ・シングルコンシューマ）です。
容量0のチャネルはアンバウンドです。

```lime
fn main():
    let ch = channel_new(10)        // 容量10のチャネルを作成

    await channel_send(ch, 42)      // 非同期送信
    let val = await channel_receive(ch)  // 非同期受信
    println(val)                    // 42

    channel_close(ch)               // チャネルを閉じる
    return
```

<!--
### Channel API
-->

### チャネルAPI

| 関数 | 説明 |
|------|------|
| `channel_new(capacity)` | チャネルを作成（0=アンバウンド） |
| `channel_send(ch, value)` | 非同期送信（`Future`） |
| `channel_receive(ch)` | 非同期受信（`Future`） |
| `channel_close(ch)` | チャネルを閉じる |

<!--
### Mutex
-->

### ミューテックス

<!--
A mutex provides mutually exclusive access to shared state. The `mutex_lock`
operation is async — if the lock is held, the task becomes `Pending` and is
woken when the lock is released.
-->

ミューテックスは共有状態への相互排他アクセスを提供します。
`mutex_lock`操作は非同期です — ロックが保持されている場合、タスクは`Pending`になり、
ロックが解放されるとwakeされます。

```lime
fn main():
    let m = mutex_new()

    await mutex_lock(m)
    // ロックを保持した状態で処理
    mutex_unlock(m)

    return
```

<!--
### Mutex API
-->

### ミューテックスAPI

| 関数 | 説明 |
|------|------|
| `mutex_new()` | ミューテックスを作成 |
| `mutex_lock(m)` | 非同期ロック取得（`Future`） |
| `mutex_unlock(m)` | ロック解放 |

<!--
### RWLock (Read-Write Lock)
-->

### RWLock（読み書きロック）

<!--
An RWLock allows multiple concurrent readers or a single writer. This is
useful when reads are frequent and writes are rare.
-->

RWLockは複数の同時読み取りまたは単一の書き込みを許可します。
読み取りが頻繁で書き込みが少ない場合に便利です。

```lime
fn main():
    let rw = rwlock_new()

    await read_lock(rw)
    // 読み取りアクセス
    read_unlock(rw)

    await write_lock(rw)
    // 書き込みアクセス
    write_unlock(rw)

    return
```

<!--
### RWLock API
-->

### RWLock API

| 関数 | 説明 |
|------|------|
| `rwlock_new()` | RWLockを作成 |
| `read_lock(rw)` | 非同期読み取りロック取得（`Future`） |
| `read_unlock(rw)` | 読み取りロック解放 |
| `write_lock(rw)` | 非同期書き込みロック取得（`Future`） |
| `write_unlock(rw)` | 書き込みロック解放 |

<!--
### Semaphore
-->

### セマフォ

<!--
A counting semaphore limits concurrent access to a resource. Tasks block
when all permits are in use.
-->

カウントセマフォはリソースへの同時アクセスを制限します。
すべての許可が使用中の場合、タスクはブロックします。

```lime
fn main():
    let sem = semaphore_new(3)   // 最大3つの同時アクセス

    await semaphore_acquire(sem)
    // リソースを使用
    semaphore_release(sem)

    return
```

<!--
### Semaphore API
-->

### セマフォAPI

| 関数 | 説明 |
|------|------|
| `semaphore_new(max)` | セマフォを作成 |
| `semaphore_acquire(sem)` | 非同期許可取得（`Future`） |
| `semaphore_release(sem)` | 許可解放 |

<!--
### Notify
-->

### ノティファイ

<!--
Notify is a low-level synchronization primitive for waking one or all waiters.
It does not hold state — a notification is consumed by exactly one waiter.
-->

Notifyは1つまたはすべての待機者をwakeするための低レベル同期プリミティブです。
状態を保持しません — 通知は正確に1つの待機者によって消費されます。

```lime
fn main():
    let n = notify_new()

    // 待機側
    await notify_wait(n)

    // 通知側
    notify_one(n)    // 待機者を1つwake
    // notify_all(n)  // すべての待機者をwake

    return
```

<!--
### Notify API
-->

### Notify API

| 関数 | 説明 |
|------|------|
| `notify_new()` | Notifyを作成 |
| `notify_wait(n)` | 非同期待機（`Future`） |
| `notify_one(n)` | 待機者を1つwake |
| `notify_all(n)` | すべての待機者をwake |

<!--
### Multi-Task Interleave
-->

### マルチタスクインタリーブ

<!--
Multiple tasks can be spawned and run cooperatively on the single-threaded
executor. Each task gets a chance to run when others `await` or `yield_now`.
-->

複数のタスクをスポーンしてシングルスレッドエグゼキュータ上で協調的に実行できます。
各タスクは他のタスクが`await`または`yield_now`を行ったときに実行機会を得ます。

```lime
lime task_a():
    let i = 0
    while i < 5:
        println("A: " + str(i))
        yield_now
        i = i + 1
    return

lime task_b():
    let i = 0
    while i < 5:
        println("B: " + str(i))
        yield_now
        i = i + 1
    return

fn main():
    spawn(task_a())
    spawn(task_b())
    // A:0, B:0, A:1, B:1, ... のように交互に実行
    return
```
