# 入门指南

## 将 Sway Libs 作为依赖项添加

要导入任何库，请在项目的`Forc.toml`文件中的`[dependencies]`下添加以下依赖项。

```sway
sway_libs = { git = "https://github.com/FuelLabs/sway-libs", tag = "v0.1.0" }
```

以下是完整的`Forc.toml`文件示例：

```sway
[project]
authors = ["Fuel Labs <contact@fuel.sh>"]
entry = "main.sw"
license = "Apache-2.0"
name = "MyProject"

[dependencies]
sway_libs = { git = "https://github.com/FuelLabs/sway-libs", tag = "v0.1.0" }
```

> **注意:** 请确保将标签设置为最新版本。

## 导入 Sway Libs 到您的项目

一旦 Sway Libs 成为项目的依赖项，您可以在您的 Sway 智能合约中导入库，如下所示：

```sway
use sway_libs::<library>::<library_function>;
```

例如，要从 Ownership 库导入`only_owner()`函数，请在您的 Sway 文件顶部使用以下语句：

```sway
use sway_libs::ownership::only_owner;
```

> **注意：**
> 所有项目目前使用`forc v0.60.0`，`fuels-rs v0.62.0`和`fuel-core 0.26.0`。

## 使用 Sway Libs

一旦您的项目已经导入所需的库，您可以调用或使用库提供的任何函数和结构。

在下面的示例中，我们导入了 Pausable 库，并为其实现了`Pausable` ABI 与其关联的函数。

```sway
use sway_libs::pausable::{_is_paused, _pause, _unpause, Pausable};

// 为我们的合约实现 Pausable ABI
impl Pausable for Contract { #[storage(write)]
fn pause() {
_pause(); // 调用提供的暂停函数。
}

    #[storage(write)]
    fn unpause() {
        _unpause(); // 调用提供的取消暂停函数。
    }

    #[storage(read)]
    fn is_paused() -> bool {
        _is_paused() // 调用提供的暂停状态函数。
    }

}
```

有关使用特定库的任何指令应在 Sway Libs 书籍的[libraries](../libraries.md)部分找到。

有关库的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/)。
