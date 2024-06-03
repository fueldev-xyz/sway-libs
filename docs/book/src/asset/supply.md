# 供应功能

有关资产库供应功能的实现详细信息，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/asset/supply/index.html)。

## 导入资产库供应功能

要使用资产库，必须将 Sway Libs 和[Sway Standards](https://github.com/FuelLabs/sway-standards)添加到`Forc.toml`文件中，然后导入到您的 Sway 项目中。要将 Sway Libs 添加为项目的依赖项，请参阅[入门](../getting_started/index.md)。要添加 Sway Standards 作为依赖项，请参阅[Sway Standards Book](https://github.com/FuelLabs/sway-standards)。

要导入资产库供应功能和[SRC-3](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)标准到您的 Sway 智能合约，请在您的 Sway 文件中添加以下内容：

```sway
{{#include ../../../../examples/asset/supply_docs/src/main.sw:import}}
```

## 与 SRC-3 标准集成

[SCR-3](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)定义规定了 Fuel 上任何原生资产都必须实现以下 abi：它们用于铸造和销毁代币。

```sway
{{#include ../../../../examples/asset/supply_docs/src/main.sw:src3_abi}}
```

资产库为`SRC3` abi 中的每个函数提供了以下补充功能：

- `_mint()`
- `_burn()`

> **注意** `_mint()` 和 `_burn()` 函数将无条件铸造和销毁资产。应应用外部检查以限制资产的铸造和销毁。

## 设置存储

一旦导入，资产库的供应功能应该可用。要使用它们，请确保将下面的存储块添加到启用[SCR-3](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)标准的合约中。

```sway
{{#include ../../../../examples/asset/supply_docs/src/main.sw:src3_storage}}
```

## 使用资产库实现 SRC-3 标准

要使用基本功能，只需传递预先定义的存储块中的`StorageKey`。下面的示例展示了如何将[SCR-3](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)标准与资产库结合使用，而不定义用户限制或自定义功能。建议与资产库的供应功能一起使用[Ownership Library](../ownership/index.md)，以确保只有一个用户具有铸造资产的权限。

```sway
{{#include ../../../../examples/asset/basic_src3/src/main.sw:basic_src3}}
```

> **注意** `_mint()` 和 `_burn()` 函数将无条件铸造和销毁资产。应应用外部检查以限制资产的铸造和销毁。
