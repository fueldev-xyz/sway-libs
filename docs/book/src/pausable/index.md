# 暂停库

暂停库允许合约实现紧急停止机制。这在诸如出现大型错误时需要一个紧急开关以冻结所有交易的情况下非常有用。

强烈建议将[拥有权库](../ownership/index.md)与暂停库结合使用，以确保只有单个管理员用户有权暂停您的合约。

有关暂停库的实现详细信息，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/pausable/index.html)。

## 导入暂停库

要使用暂停库，必须将 Sway Libs 添加到`Forc.toml`文件中，然后将其导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。

要将暂停库导入到您的 Sway 智能合约中，请在您的 Sway 文件中添加以下内容：

```sway
{{#include ../../../../examples/pausable/pausable/src/main.sw:import}}
```

## 基本功能

### 实现`Pausable` abi

暂停库有两种状态：

- `Paused`
- `Unpaused`

默认情况下，您的合约将从`Unpaused`状态开始。要暂停您的合约，您可以调用`_pause()`函数。下面的示例提供了一个使用 Pausable 库的基本可暂停合约，其中使用了 Pausable 库的`Pausable` abi，但没有任何限制，如管理员。

```sway
{{#include ../../../../examples/pausable/pausable/src/main.sw:pausable_impl}}
```

## 应用暂停限制

在开发合约时，您可能希望将函数锁定到特定状态。为此，您可以调用`require_paused()`或`require_not_paused()`函数之一。下面的示例展示了这些函数的使用。

```sway
{{#include ../../../../examples/pausable/pausable/src/main.sw:require_paused}}
```

```sway
{{#include ../../../../examples/pausable/pausable/src/main.sw:require_not_paused}}
```

## 使用拥有权库与暂停库

强烈建议将[拥有权库](../ownership/index.md)与暂停库结合使用，并将限制应用于`pause()`和`unpause()`函数。这将确保只有单个用户在紧急情况下才能暂停和取消暂停合约。如果不应用此限制，将允许任何用户阻碍合约的功能。

以下示例实现了`Pausable` abi，并对其暂停/取消暂停函数应用了限制。在此示例中，合约的所有者必须在一个名为`MyConstructor`的构造函数中设置。

```sway
{{#include ../../../../examples/pausable/pausable_with_ownership/src/main.sw:impl_with_ownership}}
```
