---
title: 编译器警告（等级1） C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: adb5c4bf3103cf98fb557a5f54b6a64013356475
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966129"
---
# <a name="compiler-warning-level-1-c4311"></a>编译器警告（等级1） C4311

“variable”: 从“type”到“type”的指针截断

此警告检测 64 位指针截断问题。 例如，如果为 64 位体系结构编译代码，则当指针被分配给 `int`（32 位）时，指针（64 位）的值将被截断。 有关详细信息，请参阅[使用指针的规则](/windows/win32/WinProg64/rules-for-using-pointers)。

有关警告 C4311 的常见原因的其他信息，请参阅[常见的编译器错误](/windows/win32/WinProg64/common-compiler-errors)。

为 64 位目标编译后，下列代码示例会生成 C4311，然后演示如何修复此问题：

```cpp
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}
```