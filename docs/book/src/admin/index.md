# 管理员库

管理员库提供了一种阻止没有“管理员状态”的用户调用合约内函数的方法。管理员库与[所有权库](../ownership/index.md)不同之处在于，可以有多个用户具有管理员状态。管理员库通常用于需要涉及多个用户或白名单的合约中进行管理调用。

此库扩展了[所有权库](../ownership/index.md)。必须导入并使用所有权库才能启用管理员库。只有合约的所有者才能添加和删除管理员用户。

有关管理员库的实现详细信息，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/admin/index.html)。

## 导入管理员库

要使用管理员库，必须将 Sway Libs 添加到`Forc.toml`文件中，然后导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。

要导入管理员库，请确保在导入语句中同时包含管理员库和所有权库。

```sway
{{#include ../../../../examples/admin/src/main.sw:import}}
```

## 将管理员库集成到所有权库中

要使用管理员库，请确保为您的合约设置了合约所有者。以下演示了如何使用[所有权库](../ownership/)设置合约所有者。

```sway
{{#include ../../../../examples/admin/src/owner_integration.sw:ownership_integration}}
```

## 基本功能

### 添加管理员

要向合约添加新的管理员，请调用`add_admin()`函数。

```sway
{{#include ../../../../examples/admin/src/main.sw:add_admin}}
```

> **注意** 只有合约的所有者才能调用此函数。请参阅上面的示例以设置合约所有者。

### 删除管理员

要从合约中删除管理员，请调用`revoke_admin()`函数。

```sway
{{#include ../../../../examples/admin/src/main.sw:remove_admin}}
```

> **注意** 只有合约的所有者才能调用此函数。请参阅上面的示例以设置合约所有者。

### 应用限制

要将函数限制为仅限管理员，请调用`only_admin()`函数。

```sway
{{#include ../../../../examples/admin/src/main.sw:only_admin}}
```

> **注意：** 管理员和合约所有者彼此独立。如果合约所有者调用了`only_admin()`，它将会回滚。

要将函数限制为仅限管理员或合约所有者，请调用`only_owner_or_admin()`函数。

```sway
{{#include ../../../../examples/admin/src/main.sw:both_admin}}
```

### 检查管理员状态

要检查用户的管理权限，请调用`is_admin()`函数。

```sway
{{#include ../../../../examples/admin/src/main.sw:check_admin}}
```
