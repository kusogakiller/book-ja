/*
## External Functions and FFI
*/

## 外部関数とFFI

<!--
`extern fn` declares a native symbol that is resolved at link time. The symbol
name is a string after the signature.
-->

`extern fn`はリンク時に解決されるネイティブシンボルを宣言します。
シンボル名はシグネチャの後の文字列です。

```lime
extern fn puts(str: msg) -> int "puts"
extern fn malloc(int: size) -> void* "malloc"
extern fn free(void*: ptr) "free"
```

<!--
### Charger FFI System
-->

### Charger FFIシステム

<!--
External functions integrate with the Charger FFI system, which can automatically
generate Lime bindings from C/C++ headers:
-->

外部関数は、C/C++ヘッダーからLimeバインディングを自動生成できる
Charger FFIシステムと統合されています:

```console
$ lime charger install /path/to/library
$ lime charger list
```

<!--
### Memory Safety Note
-->

### メモリ安全性の注意

<!--
When using external functions, you are responsible for ensuring memory safety.
Lime's type system provides some safety, but external functions bypass the
compiler's normal checks.
-->

外部関数を使用する際は、メモリの安全性を確保する責任があります。
Limeの型システムはある程度の安全性を提供しますが、外部関数はコンパイラの
通常のチェックをバイパスします。
