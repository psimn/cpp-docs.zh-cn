---
title: 安全库:C++ 标准库
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
ms.openlocfilehash: 782a3610909de01e1a1991dee3a74aee9a131da3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454551"
---
# <a name="safe-libraries-c-standard-library"></a>安全库:C++ 标准库

已对 Microsoft C++随附的库进行了多项改进, 其中包括C++标准库, 以使它们更加安全。

已将 C++ 标准库中的多个方法确定为具有潜在的不安全性，因为它们可能导致缓冲区溢出或其他代码缺陷。 建议不要使用这些方法，已创建了更安全的新方法来替代这些方法。 这些新方法均以 `_s`结尾。

还实施了多项功能增强以提升迭代器和算法的安全性。 有关详细信息，请参阅 [Checked Iterators](../standard-library/checked-iterators.md)、 [Debug Iterator Support](../standard-library/debug-iterator-support.md) 和 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>备注

下表列出了可能不安全的 C++ 标准库方法，以及更安全的等效方法：

|可能不安全的方法|更安全的等效方法|
|-------------------------------|----------------------|
|[copy](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[copy](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|

如果调用以上任何一种潜在不安全的方法或如果错误使用迭代器，则编译器将生成[编译器警告（3 级）C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 有关如何禁用这些警告的信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

## <a name="in-this-section"></a>本节内容

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Checked Iterators](../standard-library/checked-iterators.md)

[Debug Iterator Support](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>请参阅

[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)
