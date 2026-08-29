# まえがき

<!--
This book is a translated version of the original English version, adapted for
the Lime Programming Language. Lime is a small, statically-typed programming
language with a tree-walking interpreter and a native-code LLVM backend.
-->

この本は、Limeプログラミング言語に適応された、オリジナルの日本語版版です。
Limeは、ツリーウォーキングインタプリタとLLVMネイティブコードバックエンドを持つ、
小さな statically 型付きプログラミング言語です。

<!--
Lime's design principles are:
-->

Limeの設計原則は以下の通りです:

- **Easy. Simple. Fast.** — 簡単で、シンプルで、高速
- 簡潔な構文 / 読みやすさ第一
- 暗黙の型変換なし
- GCなし / コンパイラによる自動メモリ管理なし

<!--
This book teaches you how to write programs in Lime, from the basics through
more advanced features. Every construct and every example has been checked
against the current compiler.
-->

この本は、基本から高度な機能まで、Limeでプログラムを書く方法を教えます。
すべての構文とすべての例は、現在のコンパイラで確認済みです。
