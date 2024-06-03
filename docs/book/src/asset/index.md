# 资产库

资产库提供了基本的辅助函数，用于支持[SRC-20; 原生资产标准](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)、[SRC-3; 铸币和销毁标准](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)以及[SRC-7; 任意资产元数据标准](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)。它旨在使使用 Sway 开发原生资产变得快速简便，并遵循标准的规范。

有关资产库的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/asset/index.html)。

## [SRC-20 功能](./base.md)

在 Fuel Network 上的任何资产的核心或基础必须遵循[SRC-20; 原生资产标准](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)。资产库的[Base](./base.md)部分支持[SRC-20](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)的实现。

## [SRC-3 功能](supply.md)

[SRC-3; 铸币和销毁标准](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)规定了 Fuel Network 上的原生资产如何铸造和销毁的 ABI。资产库的[supply](./supply.md)部分支持[SRC-3](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)的实现。

## [SRC-7 功能](./metadata.md)

[SRC-7; 任意资产元数据标准](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)规定了与 Fuel Network 上的原生资产关联的元数据的 ABI。资产库的[metadata](./metadata.md)部分支持[SRC-7](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)的实现。
