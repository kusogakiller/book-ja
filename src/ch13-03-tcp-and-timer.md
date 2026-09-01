/*
## TCP and Timers
*/

## TCPとタイマー

<!--
Challenger includes async TCP networking and a high-resolution timer wheel
for scheduling delayed tasks.
-->

Challengerは非同期TCPネットワーキングと、遅延タスクのスケジューリングのための
高解像度タイマーホイールを含みます。

<!--
### TCP Networking
-->

### TCPネットワーキング

<!--
Challenger provides both synchronous and async TCP operations. The async
variants return futures that become `Pending` on `WOULDBLOCK` and are woken
by the reactor when I/O is ready.
-->

Challengerは同期および非同期のTCP操作を提供します。非同期バリアントは
`WOULDBLOCK`で`Pending`になり、I/Oが準備されるとreactorによってwakeされる
futureを返します。

#### ソケット作成と接続

```lime
fn main():
    let fd = tcp_socket()
    tcp_set_nonblocking(fd)
    tcp_bind(fd, "127.0.0.1", 8080)
    tcp_listen(fd, 128)

    // 非同期accept
    let client = await tcp_accept_async(fd)

    // データの送受信
    let data = await tcp_read_async(client, 1024)
    await tcp_write_async(client, data, len(data))

    tcp_close(client)
    tcp_close(fd)
    return
```

#### TCP API

| 関数 | 説明 |
|------|------|
| `tcp_socket()` | TCPソケットを作成 |
| `tcp_set_nonblocking(fd)` | 非ブロッキングモードに設定 |
| `tcp_bind(fd, host, port)` | アドレスにバインド |
| `tcp_listen(fd, backlog)` | 接続待機開始 |
| `tcp_accept(fd)` | 同期accept |
| `tcp_accept_async(fd)` | 非同期accept（`Future`） |
| `tcp_connect(fd, host, port)` | 同期connect |
| `tcp_connect_async(fd, host, port)` | 非同期connect（`Future`） |
| `tcp_read(fd, buf, len)` | 同期read |
| `tcp_read_async(fd, max_len)` | 非同期read（`Future`） |
| `tcp_write(fd, buf, len)` | 同期write |
| `tcp_write_async(fd, buf, len)` | 非同期write（`Future`） |
| `tcp_get_last_read_len()` | 最後の非同期readのバイト数を取得 |
| `tcp_get_last_read_buf()` | 最後の非同期readのデータを取得 |
| `tcp_close(fd)` | ソケットを閉じる |

<!--
### Timer
-->

### タイマー

<!--
The timer wheel provides microsecond-resolution timers. `sleep(ms)` is the
primary user-facing API — it creates a timer that wakes the current task
after the specified delay.
-->

タイマーホイールはマイクロ秒解像度のタイマーを提供します。
`sleep(ms)`は主要なユーザー向けAPIです — 指定された遅延後に現在のタスクをwakeする
タイマーを作成します。

```lime
lime periodic():
    let i = 0
    while i < 5:
        println("tick " + str(i))
        await sleep(1000)   // 1秒ごとに実行
        i = i + 1
    return
```

<!--
### Reactor
-->

### リアクター

<!--
The reactor integrates with the OS I/O notification system (IOCP on Windows,
epoll on Linux, kqueue on macOS). It monitors file descriptors and wakes
tasks when I/O operations can proceed without blocking.
-->

リアクターはOSのI/O通知システム（WindowsではIOCP、Linuxではepoll、macOSではkqueue）
と統合されています。ファイルディスクリプタを監視し、I/O操作がブロックなしで
進行できるときにタスクをwakeします。
