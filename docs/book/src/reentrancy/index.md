# 重入保护库

重入保护库提供了一个 API 来检查并防止合约的重入。重入攻击发生在一个函数在执行过程中被外部调用，使得它可以在单个事务中被多次运行。

重入检查用于检查当前调用堆栈中是否已经调用了一个合约 ID。

重入或“递归调用”攻击可能会导致某些函数以意外的方式行为。这可以通过断言在当前事务中尚未调用合约来防止。一个示例可以在[这里](https://swcregistry.io/docs/SWC-107)找到。

有关重入保护库的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/reentrancy/index.html)。

## 已知问题

虽然这可以防止单函数重入和跨函数重入攻击，但它将无法阻止跨合约重入攻击。

## 导入重入保护库

要使用重入保护库，必须将 Sway Libs 添加到`Forc.toml`文件中，然后导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。

要将重入保护库导入到您的 Sway 智能合约中，请在您的 Sway 文件中添加以下内容：

```sway
{{#include ../../../../examples/reentrancy/src/main.sw:import}}
```

## 基本功能

一旦导入，就可以通过调用以下两个函数之一来使用重入保护库：

- `is_reentrant() -> bool`
- `reentrancy_guard()`

### 使用重入保护

一旦导入，就可以通过在您的 Sway 智能合约中调用`reentrancy_guard()`来使用重入保护库。以下展示了一个应用了重入保护库的 Sway 智能合约示例：

```sway
{{#include ../../../../examples/reentrancy/src/main.sw:reentrancy_guard}}
```

### 检查重入状态

要检查当前调用者是否为重入调用者，可以调用`is_reentrant()`函数。

```sway
{{#include ../../../../examples/reentrancy/src/main.sw:is_reentrant}}
```
