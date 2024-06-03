# 库(Libraries)

Sway Libs 包含几种类型的库。这些包括提供便利函数的库、支持标准的库、数据类型库和安全功能库。

有关库的实现细节，请参阅[Sway Libs 文档](https://fuellabs.github.io/sway-libs/master/sway_libs/)。

## 资产库

资产库是任何在 Fuel Network 上使用[本地资产](https://docs.fuel.network/docs/sway/blockchain-development/native_assets)的库。

### [资产库](./asset/index.md)

[资产](./asset/index.md)库为[ SRC-20 ](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-20.md)、[ SRC-3 ](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-3.md)和 [ SRC-7 ](https://github.com/FuelLabs/sway-standards/blob/master/SRCs/src-7.md)标准提供了辅助函数。

## 访问控制和安全库

访问控制和安全库是任何旨在在开发智能合约时提供额外安全性的库。

### [所有权库(ownership)](./ownership/index.md)

[所有权(ownership)](./ownership/index.md)库用于对函数应用限制，以便只有一个**单一**用户可以调用它们。

### [管理库(admin)](./admin/index.md)

[管理(admin)](./admin/index.md)库用于对函数应用限制，以便只有少数几个用户可以调用它们，就像一个白名单。

### [暂停库(pausable)](./pausable/index.md)

[暂停(pausable)](./pausable/index.md)库允许合约实现紧急停止机制。

### [重入防范库(reentrancy)](./reentrancy/index.md)

[重入防范(reentrancy)](./reentrancy/index.md)库用于检测和防止重入攻击。

## 密码学库

密码学库是提供密码功能的库，超出了 std-lib 提供的范围。

### [字节码库](./bytecode/index.md)

[字节码(bytecode)](./bytecode/index.md)库用于在链上验证和计算合约和断言的字节码根。

### [Merkle 库](./merkle/index.md)

[Merkle 证明(Merkle Proof)](./merkle/index.md)库用于验证链下计算的二进制默克尔树。

## 数学库

数学库是提供数学函数或数字类型的库，超出了 std-lib 的范围。

### [定点数库](./fixed_point/index.md)

[定点数](./fixed_point/index.md)库是实现定点数的接口。

### [有符号整数](./signed_integers/index.md)

[有符号整数](./signed_integers/index.md)库是实现有符号整数的接口。

## 数据结构库

数据结构库提供了复杂的数据结构，为智能合约提供了额外的功能。

### [队列(queue)](./queue/index.md)

[队列(queue)](./queue/index.md)库是一个线性数据结构，提供先进先出（FIFO）操作。
