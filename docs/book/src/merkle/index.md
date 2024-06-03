# Merkle 库

Merkle 树允许在链下数据上进行链上验证。通过在链上发布 Merkle 根，可以在链下生成可验证的真实数据证明。

有关 Merkle 库的实现详细信息，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/merkle/index.html)。

## 导入 Merkle 库

要使用 Merkle 库，必须将 Sway Libs 添加到`Forc.toml`文件中，然后导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。

要将 Merkle 库导入到您的 Sway 智能合约中，请在您的 Sway 文件中添加以下内容：

```sway
{{#include ../../../../examples/merkle/src/main.sw:import}}
```

## 在 Sway 中使用 Merkle Proof 库

一旦导入，使用 Merkle Proof 库就像调用所需的函数一样简单。以下是您可以使用的函数定义列表。

- `leaf_digest()`
- `node_digest()`
- `process_proof()`
- `verify_proof()`

## 基本功能

### 计算叶子和节点

二进制证明目前允许您在给定适当的哈希摘要的情况下计算 Merkle 树的叶子和节点。

要计算叶子，请使用`leaf_digest()`函数：

```sway
{{#include ../../../../examples/merkle/src/main.sw:leaf_digest}}
```

要在给定两个叶子的情况下计算节点，请使用`node_digest()`函数：

```sway
{{#include ../../../../examples/merkle/src/main.sw:node_digest}}
```

> **注意** 计算节点时顺序很重要。

### 计算 Merkle 根

要在给定证明的情况下计算 Merkle 根，请使用`process_proof()`函数。

```sway
{{#include ../../../../examples/merkle/src/main.sw:process_proof}}
```

### 验证证明

要针对 Merkle 根验证证明，请使用`verify_proof()`函数。

```sway
{{#include ../../../../examples/merkle/src/main.sw:verify_proof}}
```

## 使用 Fuels-rs 的 Merkle Proof 库

要为您的 Sway 智能合约生成 Merkle 树和相应的证明，请使用[Fuel-Merkle](https://github.com/FuelLabs/fuel-vm/tree/master/fuel-merkle)crate。

### 导入到您的项目中

要导入 Fuel-Merkle crate，应在项目的`Cargo.toml`文件中的`[dependencies]`下添加以下内容：

```sway
fuel-merkle = { version = "0.33.0" }
```

> **注意** 确保使用最新版本的[fuel-merkle](https://crates.io/crates/fuel-merkle)crate。

### 导入到您的 Rust 文件中

要使用 Fuel-Merkle crate，应将以下内容添加到您的 Rust 文件中。

```sway
{{#include ../../../../examples/merkle/mod.rs:import}}
```

### 使用 Fuel-Merkle

#### 生成树

使用 Fuel-Merkle 创建 Merkle 树就像将叶子按增加顺序推入一样简单。

```sway
{{#include ../../../../examples/merkle/mod.rs:generating_a_tree}}
```

#### 生成和验证证明

要为特定叶子生成证明，必须具有叶子的索引或键。只需调用证明函数：

```sway
{{#include ../../../../examples/merkle/mod.rs:generating_proof}}
```

生成证明后，可以调用 Sway 智能合约的`verify_proof`函数：

```sway
{{#include ../../../../examples/merkle/mod.rs:verify_proof}}
```
