/*
## Hash Maps and Hash Sets
*/

## ハッシュマップとハッシュセット

<!--
Hash maps and hash sets are data structures that store data using keys. They
provide efficient lookup, insertion, and deletion operations.
-->

ハッシュマップとハッシュセットは、キーを使用してデータを格納するデータ構造です。
効率的な検索、挿入、削除操作を提供します。

<!--
### HashMap
-->

### HashMap

<!--
HashMaps require the `collections` package:
-->

HashMapには`collections`パッケージが必要です:

```lime
let HashMap(str, int): scores = collections.make_hash_map()
scores = scores.insert("math", 95)
scores = scores.insert("english", 88)
println(scores.get("math"))       // option.Some(...)
println(scores.contains("math"))  // true
println(scores.length())          // 2
```

<!--
### HashSet
-->

### HashSet

```lime
let HashSet(str): tags = collections.make_hash_set()
tags = tags.add("compiler")
tags = tags.add("language")
println(tags.contains("compiler"))  // true
println(tags.length())              // 2
```

<!--
### Module Functions
-->

### モジュール関数

<!--
The module forms are `collections.hashmap_insert`, `collections.hashmap_get`,
`collections.hashmap_contains_key`, etc.
-->

モジュール形式は`collections.hashmap_insert`、`collections.hashmap_get`、
`collections.hashmap_contains_key`などです。
