/*
## Tuples and Lists
*/

## タプルとリスト

<!--
Tuples and lists are two of the most important compound types in Lime. Tuples
group together values of different types into a fixed-size compound type.
Lists are growable collections of values of the same type.
-->

タプルとリストはLimeにおいて最も重要な複合型の2つです。タプルは異なる型の値を
固定サイズの複合型にまとめます。リストは同じ型の値の成長可能なコレクションです。

<!--
### Tuples
-->

### タプル

<!--
A tuple is a general way of grouping together some number of values with a
variety of types into one compound type. Tuples have a fixed length: once
declared, they cannot grow or shrink.
-->

タプルは、さまざまな型のいくつかの値を1つの複合型にまとめる一般的な方法です。
タプルは固定長です。一度宣言されると、成長も縮小もしません。

<!--
Creating a tuple:
-->

タプルを作成する:

```lime
let t = (1, "one")
```

<!--
Accessing tuple elements:
-->

タプル要素にアクセスする:

```lime
let t = (1, "one")
match t:
    try (a, b):
        println(a)   // 1
        println(b)   // one
```

<!--
Tuple patterns in match:
-->

matchでのタプルパターン:

```lime
let n = (10, (20, 30))
match n:
    try (x, (y, z)):
        println(x + y + z)
```

<!--
### Lists
-->

### リスト

<!--
A list is a collection of values of the same type. Lists are growable, meaning
you can add or remove elements. Lists use square brackets for literals.
-->

リストは同じ型の値のコレクションです。リストは成長可能で、要素を追加したり
削除したりできます。リストにはリテラルに角括弧を使用します。

```lime
let List(int): nums = []
let xs = [1, 2, 3]
let ys = ["a", "b"]
```

<!--
### List Methods
-->

### リストメソッド

<!--
Lists have several built-in methods:
-->

リストにはいくつかの組み込みメソッドがあります:

```lime
let List(int): nums = []
nums = nums.push(1)
nums = nums.push(2)
nums = nums.push(3)
println(nums)                 // [1, 2, 3]
println(nums.length())        // 3
println(nums.first())         // 1
println(nums.last())          // 3
println(nums.contains(2))     // true
println(nums.index_of(2))     // 1
println(nums.reverse())       // [3, 2, 1]
println(nums.pop())           // 3
```

<!--
> Note: List methods are non-mutating. `push` returns a new list, so you must
> reassign the binding.
-->

> 注釈: リストメソッドは不変です。`push`は新しいリストを返すので、
> バインディングを再代入する必要があります。

<!--
### List Indexing and Slicing
-->

### リストのインデックスとスライス

<!--
Indexing and slicing use the same syntax as strings:
-->

インデックスとスライスには文字列と同じ構文を使用します:

```lime
let nums = [10, 20, 30]
println(nums[0])      // 10
let sliced = nums[0:2]
println(sliced)       // Slice[10, 20]
```

<!--
### Collections Module
-->

### collectionsモジュール

<!--
The `collections` package provides additional list helpers:
-->

`collections`パッケージは追加のリストヘルパーを提供します:

```lime
let List(i): nums = [1, 2, 3]
println(collections.first(nums))    // 1
println(collections.last(nums))     // 3
println(collections.length(nums))   // 3
println(collections.contains(nums, 3))   // true
println(collections.index_of(nums, 2))   // 1
```
