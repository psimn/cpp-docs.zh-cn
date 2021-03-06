---
title: invoke_result 类
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 8cd72e62fcb65209482fd9677afcc2ec83356feb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689523"
---
# <a name="invoke_result-class"></a>invoke_result 类

确定在编译时采用指定参数类型的可调用类型的返回类型。 在 c + + 17 中添加。

## <a name="syntax"></a>语法

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>参数

可*调用*\
要查询的可调用类型。

*Args* \
供可调用类型查询的参数列表的类型。

## <a name="remarks"></a>备注

使用此模板可在编译时确定可*调用*（*args*...）的结果类型，其中，可*调用*的和*参数*中的所有类型都是任何完整类型、未知绑定的数组或可能的 cv 限定的 `void`。 类模板的 `type` 成员在使用参数*Args*... 调用时命名可*调用*的返回类型。仅当使用参数*Args*... 调用*可调用*时，才定义 `type` 成员。在未计算的上下文中。 否则，类模板没有成员 `type`，这允许在编译时对特定参数类型集进行 SFINAE 测试。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[唤醒](functional-functions.md#invoke)
