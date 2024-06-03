# 拥有权库

拥有权库提供了一种阻止除了**单个**“所有者”之外的任何人调用函数的方法。当需要单个用户对合约进行管理调用时，通常会使用拥有权库。

有关拥有权库的实现详细信息，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/ownership/index.html)。

## 导入拥有权库

要使用拥有权库，必须将 Sway Libs 和[Sway Standards](https://github.com/FuelLabs/sway-standards)添加到`Forc.toml`文件中，然后导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。要将 Sway Standards 作为依赖项添加，请参阅[Sway Standards 手册](https://github.com/FuelLabs/sway-standards)。

要将拥有权库和[SRC-5](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-5.md)标准导入到您的 Sway 智能合约中，请在您的 Sway 文件中添加以下内容：

```sway
{{#include ../../../../examples/ownership/src/main.sw:import}}
```

## 将拥有权库集成到 SRC-5 标准中

要使用拥有权库实现[SRC-5](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-5.md)标准，请确保将 Sway Standards 依赖项添加到您的合约中。以下演示了如何将拥有权库与 SRC-5 标准集成。

```sway
{{#include ../../../../examples/ownership/src/main.sw:integrate_with_src5}}
```

> **注意** 必须实现一个构造函数方法来初始化所有者。

## 基本功能

### 设置合约所有者

导入后，拥有权库的函数将可用。通过在您自己的构造函数方法中调用`initialize_ownership()`函数为您的合约初始化所有者。

```sway
{{#include ../../../../examples/ownership/src/main.sw:initialize}}
```

### 应用限制

要将函数限制为仅所有者，请调用`only_owner()`函数。

```sway
{{#include ../../../../examples/ownership/src/main.sw:only_owner}}
```

### 检查所有权状态

要从存储中返回所有权状态，请调用`_owner()`函数。

```sway
{{#include ../../../../examples/ownership/src/main.sw:state}}
```
