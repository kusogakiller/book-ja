/*
## Accepting Command Line Arguments
*/

## コマンドライン引数を受け付ける

<!--
You can access command line arguments using the `process_args()` function.
-->

`process_args()`関数を使用してコマンドライン引数にアクセスできます。

```lime
fn main():
    let args = process_args()
    println(args)
    return
```

<!--
### Running the Program
-->

### プログラムの実行

```console
$ lime run main.lime
["main.lime"]
```
