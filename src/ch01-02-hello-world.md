/*
## Hello, World!
*/

## Hello, World!

<!--
Now that you've installed Lime, let's write your first program. It's traditional
to make every programmer's first program in a new language print "Hello, world!"
to the screen. Here's a complete program that does just that.
-->

Limeがインストールされたので、最初のプログラムを書きましょう。
新しい言語での最初のプログラムは「Hello, world!」を画面に表示するのが伝統です。
以下はそのような完全なプログラムです。

<!--
Create a new file called `hello.lime` and type the following code:
-->

`hello.lime`という新しいファイルを作成し、以下のコードを入力してください:

```lime
fn main():
    println("hello, world")
    return
```

<!--
Save the file, and type the following in your terminal:
-->

ファイルを保存し、端末で以下を入力してください:

```console
$ lime run hello.lime
hello, world
```

<!--
Congratulations! You've just run your first Lime program.
-->

おめでとうございます！Limeの最初のプログラムを実行しました。

<!--
Let's break down this program in detail. Here is the first piece of the program:
-->

このプログラムを詳しく見ていきましょう。プログラムの最初の部分です:

```lime
fn main():
```

<!--
This declares a function named `main`. The `main` function is special: it is
the entry point of every executable Lime program. The first line declares a
function named `main` with no parameters, and with no return type. Note that
we've written a colon after the parentheses and an indented block follows.
-->

`main`という名前の関数を宣言しています。`main`関数は特別で、すべての実行可能なLime
プログラムのエントリポイントです。最初の行はパラメータがなく、戻り型もない
`main`という名前の関数を宣言しています。括弧の後にコロンが書き、インデントされた
ブロックが続くことに注意してください。

<!--
The body of the `main` function starts with an indented line:
-->

`main`関数の本体はインデントされた行で始まります:

```lime
    println("hello, world")
    return
```

<!--
This line prints the string `hello, world` to the screen. The `println` macro
prints the string to the screen. The `return` statement ends the function.
-->

この行は文字列`hello, world`を画面に打印します。`println`は画面に文字列を印刷します。
`return`文は関数を終了します。

<!--
### Running a Program
-->

### プログラムを実行する

<!--
You can also run a program without a `main` function. The top-level statements
still run:
-->

`main`関数なしでもプログラムを実行できます。トップレベルの文はまだ実行されます:

```lime
println("no main needed")
```

```console
$ lime run hello.lime
no main needed
```

<!--
### Type-Checking
-->

### 型チェック

<!--
You can also type-check a file without executing it:
-->

ファイルを実行せずに型チェックすることもできます:

```console
$ lime check hello.lime
ok: hello.lime type-checks cleanly
```

<!--
### Formatting
-->

### フォーマット

<!--
Lime can format your source code:
-->

Limeはソースコードをフォーマットできます:

```console
$ lime fmt hello.lime              # prints formatted source to stdout
$ lime fmt hello.lime --write      # rewrites the file in place
```
