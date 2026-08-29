/*
# Introduction
*/

# はじめに

<!--
Welcome to *The Rust Programming Language*, an introductory book about Rust.
-->

*Limeプログラミング言語*へようこそ。Limeに関する入門書です。

<!--
The Rust programming language helps you write faster, more reliable software.
-->

Limeプログラミング言語は、高速で信頼できるソフトウェアを書く手助けをしてくれます。
Limeは、簡潔な構文と高い読みやすさを重視しつつ、LLVMベースのネイティブコード生成による
高性能な実行を実現するプログラミング言語です。

<!--
## Who Lime Is For
-->

## Limeは誰のためのものなの

<!--
Lime is ideal for many people for a variety of reasons. Let's look at a few of
the most important groups.
-->

Limeは、様々な理由により多くの人にとって理想的です。

<!--
### Students
-->

### 学生

<!--
Lime is for students and those who are interested in learning about programming
concepts. Using Lime, many people have learned about topics like operating
systems development. The community is very welcoming and happy to answer
student questions.
-->

Limeは、学生やプログラミングの概念を学ぶことに興味のある方向けです。

<!--
### Companies
-->

### 企業

<!--
Lime can be used for a variety of tasks, including command line tools,
web services, and embedded applications.
-->

Limeは、コマンドラインツール、Webサービス、組み込みアプリケーションなど、
様々なタスクに使用できます。

<!--
### Open Source Developers
-->

### オープンソース開発者

<!--
Lime is for people who want to build the Lime programming language, community,
developer tools, and libraries.
-->

Limeは、Limeプログラミング言語やコミュニティ、開発者ツール、ライブラリを開発したい方向けです。

<!--
## Who This Book Is For
-->

## この本は誰のためのものなの

<!--
This book assumes that you've written code in another programming language but
doesn't make any assumptions about which one.
-->

この本は、あなたが他のプログラミング言語でコードを書いたことがあることを想定していますが、
具体的的にどの言語かという想定はしません。

<!--
## How to Use This Book
-->

## この本の使い方

<!--
In general, this book assumes that you're reading it in sequence from front to
back. Later chapters build on concepts in earlier chapters, and earlier
chapters might not delve into details on a particular topic but will revisit
the topic in a later chapter.
-->

一般的に、この本は、順番に読み進めていくことを前提にしています。後の章は、前の章の概念の上に成り立ち、
前の章では、特定の話題にさほど深入りしない可能性がありますが、後ほどの章で同じ話題を再検討するでしょう。

<!--
You'll find two kinds of chapters in this book: concept chapters and project
chapters. In concept chapters, you'll learn about an aspect of Lime. In project
chapters, we'll build small programs together, applying what you've learned so
far.
-->

この本には2種類の章があるとわかるでしょう: 概念の章とプロジェクトの章です。概念の章では、
Limeの一面を学ぶでしょう。プロジェクトの章では、それまでに学んだことを適用して一緒に小さなプログラムを構築します。

<!--
Chapter 1 explains how to install Lime, how to write a "Hello, world!" program.
Chapter 2 covers Lime features that are similar to those of other programming
languages.
-->

第1章はLimeのインストール方法、"Hello, world!"プログラムの書き方を説明します。
第2章は他のプログラミング言語の機能に似たLimeの機能を講義します。

<!--
Chapter 3 discusses tuples, lists, and strings. Chapter 4 covers structs and
methods. Chapter 5 covers enums, `match` expressions, and pattern matching.
-->

第3章ではタプル、リスト、文字列について議論します。第4章は構造体とメソッドを講義し、
第5章はenum、`match`式、パターンマッチングを講義します。

<!--
Chapter 6 covers functions and closures. Chapter 7 discusses collections.
Chapter 8 explores error handling. Chapter 9 covers generics and interfaces.
Chapter 10 covers async and await.
-->

第6章は関数とクロージャを講義し、第7章はコレクションを議論します。
第8章ではエラー処理を探究し、第9章はジェネリクスとインターフェースを講義します。
第10章はasyncとawaitを講義します。

<!--
Chapter 11 covers functional features and closures. Chapter 12 is about testing.
Chapter 13 builds an I/O project. Chapter 14 covers the standard library.
Chapter 15 covers citrus and modules.
-->

第11章は関数型機能とクロージャを講義し、第12章はテストについてです。
第13章は入出力プロジェクトを構築します。第14章は標準ライブラリを講義し、
第15章はCitrusとモジュールを講義します。

<!--
Finally, some appendices contain useful information about the language in a
more reference-like format. Appendix A covers Lime's keywords, Appendix B
covers operators and symbols, and Appendix C covers error codes.
-->

最後に、言語についての有用な情報をよりリファレンスのような形式で含む付録があります。
付録AはLimeのキーワードを講義し、付録Bは演算子と記号、付録Cはエラーコードを講義します。

<!--
There is no wrong way to read this book: if you want to skip ahead, go for it!
-->

この本を読む間違った方法なんてありません: 飛ばしたければ、どうぞご自由に！

<!--
An important part of the process of learning Lime is learning how to read the
error messages the compiler displays: these will guide you toward working code.
-->

Limeを学ぶ過程で重要な部分は、コンパイラが表示するエラーメッセージを読む方法を学ぶことです:
それは動くコードへと導いてくれます。
