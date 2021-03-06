---
title: default 命名空间
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: b67aedc791ed41e93268d9e9f44492781940d55e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740515"
---
# <a name="default-namespace"></a>default 命名空间

命名空间涵盖C++/cx 支持的内置类型`default`

## <a name="syntax"></a>语法

```
namespace default;
```

### <a name="members"></a>成员

所有内置类型都继承以下成员。

|||
|-|-|
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|确定指定的对象是否等于当前对象。|
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|返回此实例的哈希代码。|
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|返回表示当前类型的字符串。|
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|返回表示当前类型的字符串。|

### <a name="built-in-types"></a>内置类型

|name|描述|
|----------|-----------------|
|`char16`|表示 Unicode (UTF-16) 码位的 16 位非数字值。|
|`float32`|32 位 IEEE 754 浮点数。|
|`float64`|64 位 IEEE 754 浮点数。|
|`int16`|16 位带符号整数。|
|`int32`|32 位带符号整数。|
|`int64`|64 位带符号整数。|
|`int8`|8 位带符号数值。|
|`uint16`|16 位无符号整数。|
|`uint32`|32 位无符号整数。|
|`uint64`|64 位无符号整数。|
|`uint8`|8 位无符号数值。|

### <a name="requirements"></a>要求

**标头：** vccorlib.h

## <a name="see-also"></a>请参阅

[C++/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)
