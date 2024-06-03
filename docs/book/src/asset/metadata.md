# 元数据功能

有关资产库元数据功能的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/asset/metadata/index.html)。

## 导入资产库元数据功能

要使用资产库，必须将 Sway Libs 和[Sway 标准](https://github.com/FuelLabs/sway-standards)添加到`Forc.toml`文件中，然后导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。要将 Sway 标准添加为依赖项，请参阅[Sway 标准书](https://github.com/FuelLabs/sway-standards)。

要将资产库基本功能和[SRC-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)标准导入到您的 Sway 智能合约中，请将以下内容添加到您的 Sway 文件中：

\```sway
{{#include ../../../../examples/asset/metadata_docs/src/main.sw:import}}
\```

## 与 SRC-7 标准的集成

[SR-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)定义了 Fuel 上的任何原生资产所需的 ABI 实现如下：

\```sway
{{#include ../../../../examples/asset/metadata_docs/src/main.sw:src7_abi}}
\```

资产库为[SR-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)标准提供了以下补充数据类型：

- `StorageMetadata`

提供了以下附加功能，用于[SR-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)的 `Metadata` 类型：

- `as_string()`
- `is_string()`
- `as_u64()`
- `is_u64()`
- `as_bytes()`
- `is_bytes()`
- `as_b256()`
- `is_b256()`

## 设置存储

导入后，应该可以使用资产库的元数据功能。要使用它们，请确保将下面的存储块添加到您的合约中，以启用[SR-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)标准。

\```sway
{{#include ../../../../examples/asset/metadata_docs/src/main.sw:src7_storage}}
\```

## 使用 `StorageMetadata` 类型

### 设置元数据

要为资产设置一些元数据，请使用资产库提供的 `SetAssetMetadata` ABI。请务必遵循您的 `key` 的[SR-9](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-9.md)标准。建议结合使用[Ownership 库](../ownership/index.md)和 `SetAssetMetadata` ABI，以确保只有一个用户有权限设置资产的元数据。

\```sway
{{#include ../../../../examples/asset/setting_src7_attributes/src/main.sw:setting_src7_attributes}}
\```

> **注意** `_set_metadata()` 函数将*无条件*设置资产的元数据。应用外部检查以限制元数据的设置。

### 使用 StorageMetadata 实现 SRC-7 标准

要使用 `StorageMetadata` 类型，只需使用关联的 `key` 和 `AssetId` 获取存储的元数据。下面的示例显示了在没有用户定义的限制或自定义功能的情况下，与资产库的 `StorageMetadata` 类型结合使用的[SR-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)标准的实现。

\```sway
{{#include ../../../../examples/asset/basic_src7/src/main.sw:basic_src7}}
\```

## 使用 `Metadata` 扩展

[SR-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)标准定义的 `Metadata` 类型可以是以下 4 种状态之一：

```sway
pub enum Metadata {
    B256: b256,
    Bytes: Bytes,
    Int: u64,
    String: String,
}
```

资产库为 `Metadata` 类型提供了以下功能：

### `is_b256()` 和 `as_b256()`

`is_b256()` 检查使您能够检查 `Metadata` 类型是否为 `b256`。
`as_b256()` 返回 `Metadata` 类型的 `b256`。

```sway
{{#include ../../../../examples/asset/metadata_docs/src/main.sw:as_b256}}
```

### `is_bytes()` 和 `as_bytes()`

`is_bytes()` 检查使您能够检查 `Metadata` 类型是否为 `Bytes`。
`as_bytes()` 返回 `Metadata` 类型的 `Bytes`。

```sway
{{#include ../../../../examples/asset/metadata_docs/src/main.sw:as_bytes}}
```

### `is_u64()` 和 `as_u64()`

`is_u64()` 检查使您能够检查 `Metadata` 类型是否为 `u64`。
`as_u64()` 返回 `Metadata` 类型的 `u64`。

```sway
{{#include ../../../../examples/asset/metadata_docs/src/main.sw:as_u64}}
```

### `is_string()` 和 `as_string()`

`is_string()` 检查使您能够检查 `Metadata` 类型是否为 `String`。
`as_string()` 返回 `Metadata` 类型的 `String`。

```sway
{{#include ../../../../examples/asset/metadata_docs/src/main.sw:as_string}}
```
