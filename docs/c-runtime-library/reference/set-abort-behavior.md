---
title: _set_abort_behavior
ms.date: 01/02/2018
api_name:
- _set_abort_behavior
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: a63d4e77a91dafa4500d5fef8e9b5e94ee28cfbd
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948670"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

指定当程序异常终止时要采取的操作。

> [!NOTE]
> 不要使用[abort](abort.md)函数关闭 Microsoft Store 的应用程序，除非在测试或调试方案中。 根据[Microsoft Store 策略](/legal/windows/agreements/store-policies)，不允许以编程方式或 UI 方式关闭应用商店应用。 有关详细信息，请参阅[UWP 应用生命周期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>语法

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>参数

*flags*<br/>
[中止](abort.md)标志的新值。

*mask*<br/>
要设置的[中止](abort.md)标志位的掩码。

## <a name="return-value"></a>返回值

标志的旧值。

## <a name="remarks"></a>备注

有两个[中止](abort.md)标志： **_WRITE_ABORT_MSG**和 **_CALL_REPORTFAULT**。 **_WRITE_ABORT_MSG**确定在程序异常终止时是否打印有帮助的文本消息。 此消息表明应用程序已调用[abort](abort.md)函数。 默认行为是打印该消息。 **_CALL_REPORTFAULT**（如果已设置）指定在调用[abort](abort.md)时生成并报告 Watson 故障转储。 默认情况下，在非调试生成中启用故障转储报告。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>请参阅

[abort](abort.md)<br/>
