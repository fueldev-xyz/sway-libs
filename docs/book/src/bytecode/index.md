# 字节码库

字节码库允许对合约和断言的字节码根进行链上验证和计算。

合约和断言的字节码根是[二进制默克尔树](https://github.com/FuelLabs/fuel-specs/blob/master/src/protocol/cryptographic-primitives.md#binary-merkle-tree)的默克尔根，每个叶子是 16KiB 的指令。该库将计算任何合约或断言的字节码根/地址，从而允许验证部署的合约并在链上生成断言地址。

有关字节码库的实现详细信息，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/bytecode/index.html)。

## 导入字节码库

要使用字节码库，必须将 Sway Libs 添加到`Forc.toml`文件中，然后将其导入到您的 Sway 项目中。要将 Sway Libs 添加为项目的依赖项，请参阅[入门](../getting_started/index.md)。

要将字节码库导入到您的 Sway 智能合约中，请将以下内容添加到您的 Sway 文件中：

```sway
{{#include ../../../../examples/bytecode/src/main.sw:import}}
```

## 在 Sway 中使用字节码库

一旦导入，使用字节码库就像调用所需的函数一样简单。以下是您可以使用的函数定义列表。

- `compute_bytecode_root()`
- `compute_bytecode_root_with_configurables()`
- `compute_predicate_address()`
- `compute_predicate_address_with_configurables()`
- `predicate_address_from_root()`
- `swap_configurables()`
- `verify_contract_bytecode()`
- `verify_contract_bytecode_with_configurables()`
- `verify_predicate_address()`
- `verify_predicate_address_with_configurables()`

## 已知问题

请注意，如果您从 SDK 传递字节码并包含可配置的值，则提供的`Vec<u8>`字节码必须被复制以使其可变。以下内容可添加以使您的字节码可变：

```sway
{{#include ../../../../examples/bytecode/src/main.sw:known_issue}}
```

## 基本功能

下面的示例适用于内部合约调用。如果您从 SDK 传递字节码，请遵循上述已知问题中列出的步骤，以避免内存所有权错误。

## 交换可配置项

给定一些字节码，您可以通过调用`swap_configurables()`函数交换合约和断言的可配置项。

```sway
{{#include ../../../../examples/bytecode/src/main.sw:swap_configurables}}
```

## 合约

### 计算字节码根

要计算合约的字节码根，可以调用`compute_bytecode_root()`或`compute_bytecode_root_with_configurables()`函数。

```sway
{{#include ../../../../examples/bytecode/src/main.sw:compute_bytecode_root}}
```

### 验证合约的字节码根

要验证合约的字节码根，可以调用`verify_bytecode_root()`或`verify_contract_bytecode_with_configurables()`函数。

```sway
{{#include ../../../../examples/bytecode/src/main.sw:verify_contract_bytecode}}
```

## 断言

### 从字节码计算地址

要计算断言的地址，可以调用`compute_predicate_address()`或`compute_predicate_address_with_configurables()`函数。

```sway
{{#include ../../../../examples/bytecode/src/main.sw:compute_predicate_address}}
```

### 从根计算地址

如果您有断言的根，可以通过调用`predicate_address_from_root()`函数计算其相应的断言地址。

```sway
{{#include ../../../../examples/bytecode/src/main.sw:predicate_address_from_root}}
```

### 验证地址

要验证断言的地址，可以调用`verify_predicate_address()`或`verify_predicate_address_with_configurables()`函数。

```sway
{{#include ../../../../examples/bytecode/src/main.sw:verify_predicate_address}}
```
