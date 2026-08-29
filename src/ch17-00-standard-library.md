/*
## The Lime Standard Library
*/

## Limeの標準ライブラリ

<!--
Lime ships with several standard library packages. Import them in a
`citrus.toml` project.
-->

Limeにはいくつかの標準ライブラリパッケージが同梱されています。`citrus.toml`
プロジェクトでインポートしてください。

<!--
### Importing Packages
-->

### パッケージのインポート

<!--
In a `citrus.toml` project, declare imports:
-->

`citrus.toml`プロジェクトでインポートを宣言します:

```toml
[dependencies]
string = "v0.1.0"
math = "v0.1.0"
collections = "v0.1.0"
```

<!--
### Available Packages
-->

### 利用可能なパッケージ

| パッケージ | 説明 |
|---------|-------------|
| `string` | 文字列操作 |
| `math` | 数学関数 |
| `collections` | データ構造（List, Map, Set, HashMap, HashSet, Queue, Stack） |
| `io` | 標準入出力 |
| `fs` | ファイルシステム |
| `json` | JSON操作 |
| `requests` | HTTPクライアント |
| `time` | 時間操作 |
| `path` | パス操作 |
| `os` | OS情報 |
| `env` | 環境変数 |
| `process` | サブプロセス |
| `regex` | 正規表現 |
| `option` | Optionヘルパー |
| `result` | Resultヘルパー |

<!--
### Using the String Package
-->

### stringパッケージの使用

```lime
import std.string

fn main():
    println(std.string.trim("  hello  "))
    println(std.string.to_upper("abc"))
    println(std.string.contains("lime", "im"))
    return
```

<!--
### Using the Math Package
-->

### mathパッケージの使用

```lime
fn main():
    println(math.abs(-42.0))
    println(math.max(3.0, 7.0))
    println(math.min(3.0, 7.0))
    println(math.sqrt(16.0))
    println(math.pow(2.0, 10.0))
    return
```

<!--
### Using the Time Package
-->

### timeパッケージの使用

```lime
fn main():
    let Instant: start = time.now()
    let bool: slept = time.sleep(0.05)
    println(slept)
    let Duration: d = time.elapsed(start)
    println(d.secs)
    return
```

---

## 各パッケージのAPI一覧

<!--
The following sections list all available functions for each package.
-->

以下のセクションでは、各パッケージで利用可能なすべての関数を一覧します。

---

### string — 文字列操作

<!--
The string package provides functions for string manipulation. These can also
be called as methods on string values (e.g., `"hello".to_upper()`).
-->

stringパッケージは文字列操作関数を提供します。文字列値のメソッドとしても呼び出せます
（例: `"hello".to_upper()`）。

| 関数 | 説明 |
|------|------|
| `len(s)` | 文字数を返す |
| `byte_len(s)` | バイト数を返す |
| `contains(s, sub)` | 部分文字列を含むか |
| `starts_with(s, prefix)` | プレフィックスで始まるか |
| `ends_with(s, suffix)` | サフィックスで終わるか |
| `trim(s)` | 前後の空白を除去 |
| `trim_start(s)` | 先頭の空白を除去 |
| `trim_end(s)` | 末尾の空白を除去 |
| `replace(s, from, new)` | 置換 |
| `split(s, sep)` | 区切り文字で分割 |
| `slice(s, start, end)` | 部分文字列 `[start, end)` |
| `to_upper(s)` | 大文字に変換 |
| `to_lower(s)` | 小文字に変換 |
| `repeat(s, n)` | n回繰り返す |
| `find(s, sub)` | 最初の出現位置（バイトオフセット） |
| `count(s, sub)` | 出現回数 |
| `join(sep, parts)` | リストを結合 |
| `is_empty(s)` | 空文字列か |
| `to_int(s)` | 整数に変換（失敗時は0） |
| `to_float(s)` | 浮動小数点に変換（失敗時は0.0） |
| `equals(a, b)` | 大文字小文字区別的一致 |
| `compare(a, b)` | 辞書順比較（-1, 0, 1） |

```lime
import std.string

fn main():
    let s = "  Hello, Lime!  "
    println(std.string.trim(s))          // Hello, Lime!
    println(std.string.to_upper(s))      //   HELLO, LIME!
    println(std.string.contains(s, "Li")) // true
    println(std.string.split("a,b,c", ",")) // ["a", "b", "c"]
    println(std.string.join("-", ["a", "b", "c"])) // a-b-c
    println(std.string.to_int("42"))     // 42
    println(std.string.len("hello"))     // 5
    return
```

---

### math — 数学関数

<!--
The math package provides standard mathematical functions. All functions operate
on `float` values.
-->

mathパッケージは標準数学関数を提供します。すべての関数は`float`値で動作します。

| 関数 | 説明 |
|------|------|
| `abs(x)` | 絶対値 |
| `min(a, b)` | 最小値 |
| `max(a, b)` | 最大値 |
| `clamp(x, lo, hi)` | `lo`〜`hi`の範囲にクランプ |
| `sqrt(x)` | 平方根 |
| `pow(a, b)` | 累乗 `a^b` |
| `floor(x)` | 切り捨て |
| `ceil(x)` | 切り上げ |
| `round(x)` | 四捨五入 |
| `trunc(x)` | 切り捨て（0方向） |
| `exp(x)` | 指数関数 `e^x` |
| `log(x)` | 自然対数 `ln(x)` |
| `log10(x)` | 常用対数 |
| `sin(x)` | 正弦 |
| `cos(x)` | 余弦 |
| `tan(x)` | 正接 |
| `asin(x)` | 逆正弦 |
| `acos(x)` | 逆余弦 |
| `atan(x)` | 逆正接 |
| `pi()` | 円周率 π |
| `e()` | 自然対数の底 e |

```lime
fn main():
    println(math.abs(-42.0))      // 42
    println(math.sqrt(16.0))      // 4.0
    println(math.pow(2.0, 10.0))  // 1024.0
    println(math.pi())            // 3.14159...
    println(math.floor(3.7))      // 3.0
    println(math.ceil(3.2))       // 4.0
    return
```

---

### collections — データ構造

<!--
The collections package provides List, Map, Set, HashMap, HashSet, Queue, and
Stack operations.
-->

collectionsパッケージはList、Map、Set、HashMap、HashSet、Queue、Stackの操作を提供します。

#### List操作

| 関数 | 説明 |
|------|------|
| `push(list, item)` | 末尾に要素を追加（新しいリストを返す） |
| `pop(list)` | 末尾の要素を除去して返す |
| `first(list)` | 先頭要素 |
| `last(list)` | 末尾要素 |
| `length(list)` | 長さ |
| `index_of(list, item)` | 要素のインデックス（見つからない場合は-1） |
| `contains(list, item)` | 要素を含むか |
| `reverse(list)` | 逆順の新しいリスト |
| `list_insert(list, idx, item)` | 指定位置に挿入 |
| `list_set(list, idx, item)` | 指定位置の値を置換 |
| `list_get(list, idx)` | 指定位置の値を取得 |
| `list_clear(list)` | リストを空にする |
| `list_sort(list)` | ソート |
| `list_clone(list)` | ディープコピー |

```lime
fn main():
    let nums = [3, 1, 2]
    println(collections.length(nums))     // 3
    println(collections.first(nums))      // 3
    println(collections.contains(nums, 2)) // true
    let reversed = collections.reverse(nums)
    println(reversed)                     // [2, 1, 3]
    return
```

#### Map / Set操作

| 関数 | 説明 |
|------|------|
| `make_map()` | 空のMapを作成 |
| `map_insert(m, key, val)` | キー-値ペアを挿入 |
| `map_get(m, key)` | キーで値を取得（`Option`） |
| `map_contains(m, key)` | キーの存在確認 |
| `map_remove(m, key)` | キーを除去 |
| `map_len(m)` | エントリ数 |
| `make_set()` | 空のSetを作成 |
| `set_insert(s, item)` | 要素を挿入（重複不可） |
| `set_contains(s, item)` | 要素の存在確認 |
| `set_remove(s, item)` | 要素を除去 |
| `set_length(s)` | 要素数 |

#### HashMap / HashSet操作

| 関数 | 説明 |
|------|------|
| `make_hash_map()` | 空のHashMapを作成 |
| `hashmap_insert(m, key, val)` | キー-値ペアを挿入 |
| `hashmap_get(m, key)` | キーで値を取得（`Option`） |
| `hashmap_contains_key(m, key)` | キーの存在確認 |
| `hashmap_remove(m, key)` | キーを除去 |
| `hashmap_len(m)` | エントリ数 |
| `make_hash_set()` | 空のHashSetを作成 |
| `hashset_add(s, item)` | 要素を追加 |
| `hashset_contains(s, item)` | 要素の存在確認 |
| `hashset_len(s)` | 要素数 |

```lime
fn main():
    let scores = collections.make_hash_map()
    scores = collections.hashmap_insert(scores, "math", 95)
    scores = collections.hashmap_insert(scores, "english", 80)
    println(collections.hashmap_get(scores, "math"))  // Some(95)
    println(collections.hashmap_len(scores))          // 2
    return
```

#### Queue / Stack操作

<!--
Queue and Stack are backed by List. Queue is FIFO (first-in, first-out) and
Stack is LIFO (last-in, first-out).
-->

QueueとStackはListで実装されています。QueueはFIFO（先入先出）、StackはLIFO（後入先出）です。

| 関数 | 説明 |
|------|------|
| `queue_push(q, item)` | キューにエンキュー |
| `queue_pop(q)` | キューからデキュー |
| `queue_front(q)` | 先頭要素 |
| `queue_back(q)` | 末尾要素 |
| `queue_len(q)` | 長さ |
| `queue_is_empty(q)` | 空か |
| `stack_push(s, item)` | スタックにプッシュ |
| `stack_pop(s)` | スタックからポップ |
| `stack_peek(s)` | トップ要素を覗き見 |
| `stack_len(s)` | 長さ |
| `stack_is_empty(s)` | 空か |

---

### io — 標準入出力

| 関数 | 説明 |
|------|------|
| `print(s)` | 標準出力に印刷（改行なし） |
| `println(s)` | 標準出力に印刷（改行あり） |
| `eprint(s)` | 標準エラー出力に印刷（改行なし） |
| `eprintln(s)` | 標準エラー出力に印刷（改行あり） |
| `read_line()` | 標準入力から1行読み込み |
| `read_all()` | 標準入力からすべて読み込み |
| `prompt(message)` | プロンプト付きで1行読み込み |

---

### fs — ファイルシステム

| 関数 | 説明 |
|------|------|
| `read(path)` | ファイル全体を文字列として読み込み |
| `write(path, content)` | ファイルに書き込み |
| `append(path, content)` | ファイルに追記 |
| `exists(path)` | パスが存在するか |
| `remove(path)` | ファイルを削除 |
| `metadata(path)` | ファイルメタデータを取得 |
| `size(path)` | ファイルサイズ（バイト） |
| `list_dir(path)` | ディレクトリ内容をリスト |
| `create_dir(path)` | ディレクトリを作成 |
| `copy(src, dst)` | ファイルをコピー |
| `rename(src, dst)` | ファイル名を変更 |
| `is_file(path)` | ファイルか |
| `is_dir(path)` | ディレクトリか |
| `remove_dir(path)` | 空ディレクトリを削除 |
| `read_lines(path)` | ファイルを行のリストとして読み込み |
| `write_lines(path, lines)` | 行のリストをファイルに書き込み |

```lime
fn main():
    write_file("test.txt", "hello")
    let content = read_file("test.txt")
    println(content)                    // hello
    println(file_exists("test.txt"))    // true
    return
```

---

### json — JSON操作

| 関数 | 説明 |
|------|------|
| `parse(text)` | JSON文字列を解析 |
| `stringify(v)` | JSON値を文字列に変換 |
| `get(obj, key)` | キーで値を取得（`Option`） |
| `has(obj, key)` | キーの存在確認 |
| `len(v)` | 配列/オブジェクト/文字列の長さ |
| `at(arr, index)` | 配列のインデックスで要素を取得 |
| `as_string(v)` | 文字列に変換 |
| `as_int(v)` | 整数に変換 |
| `as_float(v)` | 浮動小数点に変換 |
| `as_bool(v)` | ブールに変換 |
| `null()` | null値を作成 |
| `object()` | 空のオブジェクトを作成 |
| `array()` | 空の配列を作成 |
| `set(obj, key, value)` | キー-値ペアを設定 |
| `push(arr, elem)` | 配列に要素を追加 |

---

### requests — HTTPクライアント

<!--
The requests package provides an HTTP client for making web requests.
-->

requestsパッケージはHTTPリクエストを作成するHTTPクライアントを提供します。

| 関数 | 説明 |
|------|------|
| `get(url)` | GETリクエスト |
| `post(url, body)` | POSTリクエスト |
| `put(url, body)` | PUTリクエスト |
| `patch(url, body)` | PATCHリクエスト |
| `delete(url)` | DELETEリクエスト |
| `head(url)` | HEADリクエスト |
| `options(url)` | OPTIONSリクエスト |
| `session()` | セッションを作成 |
| `request(method, url)` | リクエストビルダーを作成 |

#### Response方法

| メソッド | 説明 |
|---------|------|
| `Response.status()` | HTTPステータスコード |
| `Response.text()` | レスポンスボディを文字列で |
| `Response.json()` | レスポンスボディをJSONで |
| `Response.ok()` | ステータスが2xxか |
| `Response.headers()` | レスポンスヘッダー |

---

### time — 時間操作

<!--
The time package provides functions for working with time. `Instant` represents
a point in time, and `Duration` represents a span of time.
-->

timeパッケージは時間操作関数を提供します。`Instant`はある時点を、`Duration`は時間を表します。

| 関数 | 説明 |
|------|------|
| `now()` | 現在時刻（`Instant`） |
| `elapsed(start)` | 経過時間（`Duration`） |
| `sleep(secs)` | 指定秒数スリープ |

```lime
fn main():
    let Instant: start = time.now()
    time.sleep(0.1)
    let Duration: d = time.elapsed(start)
    println(d.secs)
    return
```

---

### path — パス操作

| 関数 | 説明 |
|------|------|
| `join(a, b)` | パスを結合 |
| `basename(path)` | 最終コンポーネント（ファイル名） |
| `dirname(path)` | ディレクトリ部分 |
| `filename(path)` | 拡張子なしのファイル名 |
| `extension(path)` | 拡張子（ドット付き） |
| `is_absolute(path)` | 絶対パスか |
| `normalize(path)` | `.`と`..`を解決 |
| `equals(a, b)` | パスの論理的等価性 |
| `parent(path)` | 親ディレクトリ |

---

### os — OS情報

| 関数 | 説明 |
|------|------|
| `name()` | OS名（例: "windows", "linux"） |
| `arch()` | CPUアーキテクチャ（例: "x86_64"） |
| `platform()` | プラットフォーム |
| `hostname()` | マシンホスト名 |
| `cwd()` | カレントワーキングディレクトリ |
| `set_cwd(path)` | カレントディレクトリを変更 |

---

### env — 環境変数

| 関数 | 説明 |
|------|------|
| `get(key)` | 環境変数を取得（`Option`） |
| `has(key)` | 環境変数の存在確認 |
| `set(key, value)` | 環境変数を設定 |
| `remove(key)` | 環境変数を削除 |
| `all()` | すべての環境変数（`Map`） |

---

### process — サブプロセス

| 関数 | 説明 |
|------|------|
| `spawn(cmd, args)` | プロセスを起動（待機なし） |
| `run(cmd, args)` | プロセスを実行して待機 |
| `output(cmd, args)` | プロセスを実行しstdoutを返す |
| `wait(handle)` | プロセスの終了を待機 |
| `kill(handle)` | プロセスを終了 |
| `status(handle)` | プロセスの状態 |
| `args()` | 現在のプログラムのコマンドライン引数 |

---

### regex — 正規表現

| 関数 | 説明 |
|------|------|
| `is_match(pattern, text)` | 完全一致パターン検証 |
| `find(pattern, text)` | 最初の一致を検索 |
| `find_all(pattern, text)` | すべての一致を検索 |
| `replace(pattern, text, replacement)` | 最初の一致を置換 |
| `replace_all(pattern, text, replacement)` | すべての一致を置換 |
| `split(pattern, text)` | パターンで分割 |

---

### option — Optionヘルパー

| 関数 | 説明 |
|------|------|
| `is_some(opt)` | `Some`か |
| `is_none(opt)` | `None`か |
| `extract(opt)` | 値を取り出す（`None`の場合はpanic） |
| `extract_or(opt, default)` | 値を取り出す（`None`の場合はデフォルト値） |

---

### result — Resultヘルパー

| 関数 | 説明 |
|------|------|
| `is_ok(res)` | `Success`か |
| `is_err(res)` | `Error`か |
| `extract(res)` | 値を取り出す（`Error`の場合はpanic） |
| `extract_or(res, default)` | 値を取り出す（`Error`の場合はデフォルト値） |

---

## 組み込み関数

<!--
In addition to the package functions above, Lime provides several global
built-in functions that can be called without importing any package.
-->

上記のパッケージ関数に加え、Limeはパッケージのインポートなしで呼び出せる
グローバル組み込み関数を提供します。

| 関数 | 説明 |
|------|------|
| `println(...args)` | 標準出力に印刷（改行あり） |
| `print(...args)` | 標準出力に印刷（改行なし） |
| `eprintln(...args)` | 標準エラー出力に印刷（改行あり） |
| `eprint(...args)` | 標準エラー出力に印刷（改行なし） |
| `input(prompt)` | プロンプト付きで1行読み込み |
| `panic(msg)` | メッセージ付きでプログラムを中断 |
| `int(val)` | `int`型に変換 |
| `float(val)` | `float`型に変換 |
| `str(val)` | `str`型に変換 |
| `len(val)` | 文字列のバイト長またはリストの長さ |
| `read_file(path)` | ファイルを読み込み |
| `write_file(path, content)` | ファイルに書き込み |
| `append_file(path, content)` | ファイルに追記 |
| `file_exists(path)` | ファイルの存在確認 |
| `remove_file(path)` | ファイルを削除 |
| `process_args()` | コマンドライン引数のリスト |
| `StringBuilder()` | 文字列ビルドアを作成 |
