# 固定小数点数库

固定小数点数库提供了在 Sway 中使用固定小数点数的库。它有 3 种不同的无符号类型：`UFP32`、`UFP64`和`UFP128`，以及 3 种有符号类型`IFP64`、`IFP128`和`IFP256`。这些类型是栈分配的。

这种类型在底层存储为`u32`、`u64`或`U128`。因此，大小可以在编译时知道，长度是静态的。

有关固定小数点数库的实现详细信息，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/fixed_point/index.html)。

## 导入固定小数点数库

要使用固定小数点数库，必须将 Sway Libs 添加到`Forc.toml`文件中，然后将其导入到您的 Sway 项目中。要将 Sway Libs 添加为项目的依赖项，请参阅[入门](../getting_started/index.md)。

要将固定小数点数库导入到您的 Sway 智能合约中，请将以下内容添加到您的 Sway 文件中：

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:import}}
```

## 支持的固定小数点数

### 有符号固定小数点数

我们目前支持以下有符号固定小数点数：

- `IFP64`
- `IFP128`
- `IFP256`

要使用`IFP64`、`IFP128`或`IFP256`类型，请像这样将其导入到您的 Sway 项目中：

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:import_ifp}}
```

### 无符号固定小数点数

我们目前支持以下无符号固定小数点数：

- `UFP32`
- `UFP64`
- `UFP128`

要使用`UFP32`、`UFP64`或`UFP128`类型，请像这样将其导入到您的 Sway 项目中：

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:import_ufp}}
```

## 基本功能

### 实例化新的固定小数点数

一旦导入，任何有符号或无符号固定小数点数类型都可以通过定义一个新变量并调用`from`函数来实例化。

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:instantiating_ufp}}
```

### 基本数学函数

基本算术运算像平常一样工作。

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:mathematical_ops}}
```

### 支持的高级数学函数

我们目前支持以下高级数学函数：

#### 指数

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:exponential}}
```

#### 平方根

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:square_root}}
```

#### 幂

```sway
{{#include ../../../../examples/fixed_point/src/main.sw:power}}
```
