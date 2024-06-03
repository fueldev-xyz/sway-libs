# 基本功能

有关资产库基本功能的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/asset/base/index.html)。

## 导入资产库基本功能

要使用资产库，必须将 Sway Libs 和[Sway 标准](https://github.com/FuelLabs/sway-standards)添加到`Forc.toml`文件中，然后导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。要将 Sway 标准添加为依赖项，请参阅[Sway 标准书](https://github.com/FuelLabs/sway-standards)。

要将资产库基本功能和[SRC-20](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)标准导入到您的 Sway 智能合约中，请将以下内容添加到您的 Sway 文件中：

```sway
{{#include ../../../../examples/asset/base_docs/src/main.sw:import}}
```

## 与 SRC-20 标准的集成

[SR-20](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)定义了 Fuel 上的任何原生资产所需的 ABI 实现如下：

```sway
{{#include ../../../../examples/asset/base_docs/src/main.sw:src20_abi}}
```

资产库为`SRC20` abi 中的每个函数提供了以下补充功能：

- `_total_assets()`
- `_total_supply()`
- `_name()`
- `_symbol()`
- `_decimals()`

还提供了以下 ABI 和函数来设置您的[SRC-20](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)标准存储值：

```sway
{{#include ../../../../examples/asset/base_docs/src/main.sw:set_attributes}}
```

- `_set_name()`
- `_set_symbol()`
- `_set_decimals()`

> **注意** `_set_name()`、`_set_symbol()` 和 `_set_decimals()` 函数将*无条件*设置资产的属性。应用外部检查以限制属性的设置。

## 设置存储

导入后，应该可以使用资产库的基本功能。为了使用它们，请确保将下面的存储块添加到您的合约中，以启用[SRC-20](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)标准。

```sway
{{#include ../../../../examples/asset/base_docs/src/main.sw:src20_storage}}
```

## 使用资产库实现 SRC-20 标准

要使用资产库的基本功能，只需传递预定义存储块中的 `StorageKey`。下面的示例显示了在没有用户定义的限制或自定义功能的情况下，与资产库结合使用的[SRC-20](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)标准的实现。

```sway
{{#include ../../../../examples/asset/basic_src20/src/main.sw:basic_src20}}
```

## 设置资产的 SRC-20 属性

要为资产设置一些属性，请使用资产库提供的 `SetAssetAttributes` ABI。下面的示例显示了在没有用户定义的限制或自定义功能的情况下，使用 `SetAssetAttributes` ABI 的实现。建议结合使用[Ownership 库](../ownership/index.md)和`SetAssetAttributes` ABI，以确保只有一个用户有权限设置资产的属性。

```sway
{{#include ../../../../examples/asset/setting_src20_attributes/src/main.sw:setting_src20_attributes}}
```

> **注意** `_set_name()`、`_set_symbol()` 和 `_set_decimals()` 函数将*无条件*设置资产的属性。应用外部检查以限制属性的设置。
