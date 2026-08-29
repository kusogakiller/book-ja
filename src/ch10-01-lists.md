/*
## Lists
*/

## リスト

<!--
A list is a collection of values of the same type that can grow or shrink.
Lists are the most common collection in Lime.
-->

リストは成長または縮小できる同じ型の値のコレクションです。
リストはLimeで最も一般的なコレクションです。

<!--
### Creating Lists
-->

### リストの作成

```lime
let List(int): nums = []
let xs = [1, 2, 3]
let ys = ["a", "b"]
```

<!--
### List Methods
-->

### リストメソッド

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
```

<!--
### Indexing and Slicing
-->

### インデックスとスライス

```lime
let nums = [10, 20, 30]
println(nums[0])      // 10
let sliced = nums[0:2]
println(sliced)       // Slice[10, 20]
```
