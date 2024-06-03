# 有符号整数库

有符号整数库提供了在 Sway 中使用有符号数字的功能。它包含了 6 种不同的类型：`I8`、`I16`、`I32`、`I64`、`I128` 和 `I256`。这些类型是栈分配的。

这些类型被存储为无符号整数，因此要么是 `u64`，要么是多个 `u64`。因此，大小在编译时可以确定，长度是静态的。

有关有符号整数库的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/signed_integers/index.html)。

## 导入有符号整数库

为了使用有符号整数库，必须将 Sway Libs 添加到 `Forc.toml` 文件中，并将其导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到 `Forc.toml` 文件中，请参阅[入门指南](../getting_started/index.md)。

要将有符号整数库导入到您的 Sway 智能合约中，请在您的 Sway 文件中添加以下内容：

\```sway
{{#include ../../../../examples/signed_integers/src/main.sw:import}}
\```

要使用任何有符号整数类型之一，请像下面这样将它们导入到您的 Sway 项目中：

\```sway
{{#include ../../../../examples/signed_integers/src/main.sw:import_8}}
\```

## 基本功能

### 实例化一个新的有符号整数

一旦导入，可以通过定义一个新变量并调用 `new` 函数来实例化一个 `有符号整数` 类型。

\```sway
{{#include ../../../../examples/signed_integers/src/main.sw:initialize}}
\```

### 基本数学运算

基本的算术运算可以像通常一样工作。

\```sway
{{#include ../../../../examples/signed_integers/src/main.sw:mathematical_ops}}
\```

## 已知问题

目前 `I128` 的实现在执行数学计算时会编译出大的字节码大小。因此，`I128` 和 `I256` 会继承相同的问题，并可能导致较高的交易成本。这应该在未来对 Sway 编译器的优化中得到解决。
