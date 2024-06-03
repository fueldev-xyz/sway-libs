# 队列库

队列是一种遵循先进先出（FIFO）原则的线性结构。这意味着先添加的元素是先被移除的元素。

有关队列库的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/queue/index.html)。

## 导入队列库

要使用队列库，必须将 Sway Libs 添加到`Forc.toml`文件中，然后将其导入到您的 Sway 项目中。要将 Sway Libs 作为项目的依赖项添加到`Forc.toml`文件中，请参阅[入门指南](../getting_started/index.md)。

要将队列库导入到您的 Sway 智能合约中，请在您的 Sway 文件中添加以下内容：

```sway
{{#include ../../../../examples/queue/src/main.sw:import}}
```

## 基本功能

### 实例化新队列

一旦导入了`Queue`，您可以通过调用`new`函数创建一个新的队列实例。

```sway
{{#include ../../../../examples/queue/src/main.sw:instantiate}}
```

## 入队元素

使用`enqueue`函数可以向`Queue`添加元素。

```sway
{{#include ../../../../examples/queue/src/main.sw:enqueue}}
```

### 出队元素

要从`Queue`中移除元素，使用`dequeue`函数。此函数遵循 FIFO 原则。

```sway
{{#include ../../../../examples/queue/src/main.sw:dequeue}}
```

### 获取头部元素

要检索`Queue`头部的元素而不将其删除，可以使用`peek`函数。

```sway
{{#include ../../../../examples/queue/src/main.sw:peek}}
```

### 检查队列的长度

可以使用`is_empty`和`len`函数来检查队列是否为空，并分别获取队列中的元素数量。

```sway
{{#include ../../../../examples/queue/src/main.sw:length}}
```
