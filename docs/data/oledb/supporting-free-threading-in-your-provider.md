---
title: 在提供程序中支持自由线程处理
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: a2afb7354dd0447375ee6205b7c5d9a4755aa4b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404489"
---
# <a name="supporting-free-threading-in-your-provider"></a>在提供程序中支持自由线程处理

所有 OLE DB 提供程序类都是线程安全的并相应地设置注册表项。 它是性能的一个好办法支持自由线程处理，以帮助提供高级别的多用户环境下。 为了帮助保持您的提供程序线程安全，必须验证你的代码正确阻止。 每次写入或存储数据，必须阻止使用临界区的访问权限。

每个 OLE DB 提供程序模板对象都有其自己的关键部分。 若要使模块化更容易，您创建的每个新类应将父类的模板类名称作为参数。

下面的示例演示如何阻止你的代码：

```cpp
template <class T>
class CMyObject<T> : public...

HRESULT MyObject::MyMethod(void)
{
   T* pT = (T*)this;      // this gets the parent class

// You don't need to do anything if you are only reading information

// If you want to write information, do the following:
   pT->Lock();         // engages critical section in the object
   ...;                // write whatever information you wish
   pT->Unlock();       // disengages the critical section
}
```

详细了解如何保护包含的关键部分`Lock`并`Unlock`，请参阅[多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

验证您覆盖任何方法 (如`Execute`) 是线程安全的。

## <a name="see-also"></a>请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)